<template>
  <section id="blue-jays" class="card card--small-view">
    <BlueJaysTeam :team="score.teams[0]"></BlueJaysTeam>
    <BlueJaysTeam :team="score.teams[1]"></BlueJaysTeam>
    <p class="game-status">{{ played ? score.status : `${score.time} ${score.ampm}` }}</p>
  </section>
</template>

<script>
import BlueJaysTeam from './BlueJaysTeam'

export default {
  name: 'BlueJays',
  components: {
    BlueJaysTeam
  },
  data () {
    return {
      played: true,
      score: {
        teams: [
          {
            visitiness: 'away',
            win: '',
            loss: '',
            team_city: '',
            team_name: '',
            team_runs: '',
            name_abbrev: ''
          },
          {
            visitiness: 'home',
            win: '',
            loss: '',
            team_city: '',
            team_name: '',
            team_runs: '',
            name_abbrev: ''
          }
        ],
        status: '',
        time: '',
        ampm: ''
      }
    }
  },
  methods: {
    getScore () {
      // const date = new Date()
      // const path = `year_${date.getFullYear()}/month_${date.getMonth() + 1}/day_${date.getDate()}/miniscoreboard.json`
      const path = `year_2017/month_04/day_25/miniscoreboard.json`
      fetch(`http://gd2.mlb.com/components/game/mlb/${path}`)
        .then(async res => {
          let data = await res.json()
          data = data.data.games.game.filter(obj => {
            return (obj.away_name_abbrev === 'TOR' || obj.home_name_abbrev === 'TOR')
          })[0]
          for (let team of this.score.teams) {
            for (let prop in team) {
              if (prop === 'visitiness') continue
              let key = `${team.visitiness}_${prop}`
              team[prop] = data[key]
            }
          }
          this.score.status = data.status
          this.score.time = data.time
          this.score.ampm = data.ampm
        })
        .catch(err => { console.log(err) })
      this.setStatus()
    },
    setStatus () {
      // TO-DO: find out what unplayed state is
    }
  },
  mounted () {
    this.getScore()
  }
}
</script>

<style>

</style>

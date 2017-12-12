<template>
  <section id="blue-jays" class="card card--small-view">
    <figure class="score__team">
      <div class="score___team-info">
        <h2 class="score___team-name">{{ `${score.away_team_city} ${score.away_team_name}` }}</h2>
        <p class="score___team-record">{{ score.away_win }} - {{ score.away_loss }}</p>
      </div>
      <div class="score__team-runs">{{ score.away_team_runs }}</div>
    </figure>
    <figure class="score__team">
      <div class="score___team-info">
        <h2 class="score___team-name">{{ score.home_team_city + ' ' + score.home_team_name }}</h2>
        <p class="score___team-record">{{ score.home_win }} - {{ score.home_loss }}</p>
      </div>
      <div class="score__team-runs">{{ score.home_team_runs }}</div>
    </figure>
    <p class="game-status">{{ played ? score.status : `${score.time} ${score.ampm}` }}</p>
  </section>
</template>

<script>
export default {
  name: 'BlueJays',
  data () {
    return {
      played: true,
      score: {
        away_win: '',
        away_loss: '',
        away_team_city: '',
        away_team_name: '',
        away_team_runs: '',
        home_win: '',
        home_loss: '',
        home_team_city: '',
        home_team_name: '',
        home_team_runs: '',
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
      const path = `year_2017/month_06/day_05/miniscoreboard.json`
      fetch(`http://gd2.mlb.com/components/game/mlb/${path}`)
        .then(async res => {
          const data = await res.json()
          this.score = data.data.games.game.filter(obj => {
            return (obj.away_name_abbrev === 'TOR' || obj.home_name_abbrev === 'TOR')
          })[0]
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

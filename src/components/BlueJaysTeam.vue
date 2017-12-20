<template>
  <div class="score__team">
    <img :src="`/assets/mlb/${team.name_abbrev}.png`" :alt="team.team_name" class="score__team-logo">
    <div class="score__team-info">
      <h2 class="score__team-name">{{ team.team_city }} {{ checkAbbrev() ? team.team_name : null }}</h2>
      <p class="score__team-record">{{ team.win }} - {{ team.loss }} <span class="score__gb">{{ team.games_back }}</span></p>
    </div>
    <div class="score__team-runs">{{ team.team_runs }}</div>
  </div>
</template>

<script>
export default {
  name: 'BlueJaysTeam',
  props: {
    team: {
      type: Object,
      required: true
    }
  },
  methods: {
    checkAbbrev () {
      let displayName = true

      switch (this.team.name_abbrev) {
        case 'NYY':
          displayName = false
          break
        case 'LAA':
          displayName = false
          break
        case 'CHW':
          displayName = false
          break
        case 'NYM':
          displayName = false
          break
        case 'LAD':
          displayName = false
          break
        case 'CHC':
          displayName = false
          break
        default:
          displayName = true
      }

      return displayName
    }
  },
  data () {
    return {}
  }
}
</script>

<style>
.score__team {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  grid-gap: 20px;
  align-items: center;
  margin-bottom: 20px;
}
.score__team-logo {
  max-width: 100%;
}
.score__team-name {
  font-size: 22px;
}
.score__team-runs {
  font-size: 72px;
  line-height: 1em;
  text-align: right;
}
</style>

<template>
  <div class="score__team">
    <img :src="`./static/mlb/${team.name_abbrev.toLowerCase()}.png`" :alt="team.team_name" class="score__team-logo">
    <div class="score__team-info">
      <h2 class="score__team-name subtitle">{{ team.team_city }} {{ checkAbbrev() ? team.team_name : null }}</h2>
      <p class="score__team-record small-data">{{ team.win }} - {{ team.loss }} <span class="score__gb">{{ team.games_back }}</span></p>
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

<style lang="scss">
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

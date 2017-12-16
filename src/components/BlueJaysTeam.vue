<template>
  <div class="score__team">
    <div class="score___team-info">
      <h2 class="score___team-name">{{ `${team.team_city} ${team.team_name}` }}</h2>
      <p class="score___team-record">{{ team.win }} - {{ team.loss }} <span class="score__gb">{{ team.games_back }}</span></p>
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
  data () {
    return {}
  }
}
</script>

<style>

</style>

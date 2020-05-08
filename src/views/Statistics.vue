<template>
  <div class="statistics-page">
    <h1>Statistics</h1>
    <div class="card-statistics-wrap" v-for="(log, index) in logs" :key="index">
      <div class="card"><p>{{log.name}}</p></div>
      <div class="chart-wrap">
        <div class="first_block"></div>
        <div class="x-axis">
          <div class="statistics-card"
               :style="{'height': + Math.abs(value) * 40 + 'px',
               'bottom': + value * 40 + 'px',
               'left': + index * 60 + 'px'}"
               :class="value < 0? 'red':'green'"
               v-for="(value, index) in log.val"
               :key="index">{{value}}</div>
        </div>
        <div class="second_block"></div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Statistics',
    data() {
      return {
        logs: []
      }
    },
    mounted () {
      this.logs = JSON.parse(localStorage.getItem('logs'))
    }
  }
</script>

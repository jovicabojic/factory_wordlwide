<template>
  <div class="pieChartWrap">
    <h1>This is an about page</h1>
    <div class="" v-for="(log, index) in logs" :key="index">
      {{log.name}}
      <chart :data="chartData" :options="options"></chart>
    </div>
  </div>
</template>

<script>
  import Chart from "../components/Chart.vue"
  export default {
    name: 'Statistics',
    data() {
      return {
        logs: [],
        chartData: {
          labels: [2,4],
          datasets: [
            {
              backgroundColor: ["#228b22", "#ed143d"],
              borderWidth: 0,
              data: [3,5]
            }
          ]
        },
        options: {
          layout: {
            padding: 20
          },
          legend: {
            display: false
          },
          responsive: true,
          maintainAspectRatio: false,
        },
        window: {
          devicePixelRatio: 0.2
        },
      }
    },
    created() {
    },
    mounted () {
      this.logs = JSON.parse(localStorage.getItem('logs'))
    },
    components: {
      Chart
    },
  }
</script>

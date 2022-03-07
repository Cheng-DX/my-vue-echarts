<template>
  <div style="height: 400px;width: 600px">
    <d-chart fast-mode :x-data="x" :series="series" />
  </div>
</template>

<script>
import DChart from "../src/dchart.vue"
export default {
  name: "optionDemo",
  components: {
    DChart,
  },
  data() {
    return {
      x: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
      series: [
        {
          name: 'Email',
          data: [120, 132, 101, 134, 90, 230, 210]
        },
        {
          name: 'Union Ads',
          data: [220, 182, 191, 234, 290, 330, 310]
        },
        {
          name: 'Video Ads',
          data: [150, 232, 201, 154, 190, 330, 410]
        },
        {
          name: 'Direct',
          data: [320, 332, 301, 334, 390, 330, 320]
        },
        {
          name: 'Search Engine',
          data: [820, 932, 901, 934, 1290, 1330, 1320]
        }
      ]
    }
  },
  created() {
    this.series.forEach(item => {
      item.stack = 'Total'
      item.areaStyle = {}
    })
  }
}
</script>

<style>
</style>
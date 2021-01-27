<template>
  <div class="chart-container" id="main"></div>
</template>

<script>
import * as echarts from "echarts";

export default {
  data() {
    return {
      myChart: null,
    };
  },

  computed: {},

  mounted() {
    this.loadChart();
  },

  methods: {
    loadChart() {
      this.myChart = echarts.init(document.getElementById("main"));
      // 绘制图表
      var xAxisData = [];
      var data1 = [];
      var data2 = [];
      for (var i = 0; i < 51; i++) {
        xAxisData.push("Day" + i);
        data1.push((Math.sin(i / 5) * (i / 5 - 10) + i / 6) * 5);
        data2.push((Math.cos(i / 5) * (i / 5 - 10) + i / 6) * 5);
      }

      var option = {
        title: {
          text: "",
        },
        legend: {
          data: ["心态", "收获"],
        },
        tooltip: {},
        xAxis: {
          data: xAxisData,
          splitLine: {
            show: false,
          },
        },
        yAxis: {},
        series: [
          {
            name: "心态",
            type: "bar",
            data: data1,
            emphasis: {
              focus: "series",
            },
            animationDelay: function (idx) {
              return idx * 15;
            },
          },
          {
            name: "收获",
            type: "bar",
            data: data2,
            emphasis: {
              focus: "series",
            },
            animationDelay: function (idx) {
              return idx * 15 + 100;
            },
          },
        ],
        animationEasing: "elasticOut",
        animationDelayUpdate: function (idx) {
          return idx * 5;
        },
      };
      this.myChart.setOption(option);
      window.addEventListener("resize", () => this.myChart.resize(), false);
    },
  },
};
</script>
<style lang='scss' scoped>
.chart {
  &-container {
    width: 100%;
    height: 100%;
  }
}
</style>
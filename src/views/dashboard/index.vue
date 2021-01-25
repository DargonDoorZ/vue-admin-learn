<template>
  <div class="dashboard-container">
    <div id="main" class="dashboard-text" />
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import * as echarts from "echarts";
export default {
  name: "Dashboard",
  computed: {
    ...mapGetters(["name"]),
  },
  data() {
    return {
      myChart: null,
    };
  },
  mounted() {
    this.loadChart();
  },
  methods: {
    loadChart() {
      this.myChart = echarts.init(document.getElementById("main"));
      // 绘制图表
      this.myChart.setOption({
        title: {
          text: "ECharts",
        },
        tooltip: {},
        xAxis: {
          data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "野餐"],
        },
        yAxis: {},
        series: [
          {
            name: "销量",
            type: "bar",
            data: [5, 20, 36, 10, 10, 20],
          },
        ],
      });
      this.myChart.resize();
      window.removeEventListener("resize", () => _handleResize, false);
      window.addEventListener("resize", _handleResize, false);
      const _that = this;
      function _handleResize() {
        _that.myChart.resize();
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
    width: 100%;
    height: 600px;
  }
}
</style>

<template>
  <div class="dashboard-container">
    <!-- <div class="dashboard-text">{{ name }}</div>
    <div class="dashboard-chart">
      <DelayChart />
    </div> -->
    <div class="dashboard-carousel">
      <el-carousel :interval="4000" type="card" height="200px">
        <el-carousel-item v-for="item in 6" :key="item">
          <h3 class="medium">{{ item }}</h3>
        </el-carousel-item>
      </el-carousel>
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import DelayChart from "@/components/dashBoard/DelayChart";
export default {
  name: "Dashboard",
  computed: {
    ...mapGetters(["name"]),
  },
  data() {
    return {};
  },
  components: { DelayChart },
  mounted() {},
  methods: {},
};
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding-top: 16px;
  }
  &-chart {
    width: 500px;
    height: 300px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
  &-carousel {
    width: 80%;
  }
}
</style>
<style lang="scss">
.dashboard {
  &-carousel {
    .el-carousel__item h3 {
      color: #475669;
      font-size: 14px;
      opacity: 0.75;
      line-height: 200px;
      margin: 0;
    }
    .el-carousel__item:nth-child(2n) {
      background-color: #99a9bf;
    }

    .el-carousel__item:nth-child(2n + 1) {
      background-color: #d3dce6;
    }
  }
}
</style>
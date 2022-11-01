<template>
  <div class="container">
    <!-- 左侧布局 -->
    <div class="lay left_lay">
      <!-- 柱状图-就业行业 -->
      <JobData />
      <!-- 折线图-人员变化 -->
      <PeopleChange />
      <!-- 饼状图-年龄分布 -->
      <AgeDistribution />
    </div>
    <!-- 中间布局 -->
    <div class="middle_lay">
      <!-- 数据信息展示 -->
      <DataInfo />
    </div>
    <!-- 右侧布局 -->
    <div class="lay right_lay">
      <!-- 柱状图-技能掌握 -->
      <MasterAbility />
      <!-- 折线图-播放量 -->
      <PlayAmount />
      <!-- 饼状图-地区分布 -->
      <AreaDistribution />
    </div>

    <!-- 高德地图 -->
    <div class="map">
      <GaodeMap />
    </div>
  </div>
</template>

<script setup lang="ts">
import GaodeMap from "./components/GaodeMap.vue";
import JobData from "./components/JobData.vue";
import PeopleChange from "./components/PeopleChange.vue";
import AgeDistribution from "./components/AgeDistribution.vue";
import DataInfo from "./components/DataInfo.vue";
import MasterAbility from "./components/MasterAbility.vue";
import PlayAmount from "./components/PlayAmount.vue";
import AreaDistribution from "./components/AreaDistribution.vue";
</script>

<style lang="less" scoped>
.container {
  width: 100vw;
  position: relative;
  overflow: hidden;
  .lay {
    position: absolute;
    height: 100%;
    z-index: 999;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }
  .left_lay {
    width: 30%;
    left: 0;
    opacity: 0.5;
  }
  .middle_lay {
    padding: 0 5px;
    width: 40%;
    height: 15%;
    position: absolute;
    left: 30%;
    opacity: 0.5;
    z-index: 999;
  }
  .right_lay {
    width: 30%;
    right: 0;
    opacity: 0.5;
  }
}
</style>

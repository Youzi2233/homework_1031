<template>
  <div class="data_info">
    <BorderBox10>
      <div class="info_box">
        <!-- 前期需求人数 -->
        <div class="need_people">
          <h1>125811</h1>
          <span>前期需求人数</span>
        </div>
        <!-- 市场供应人数 -->
        <div class="supply_people">
          <h1>125811</h1>
          <span>市场供应人数</span>
        </div>
      </div>
    </BorderBox10>
  </div>
</template>

<script setup lang="ts">
import { BorderBox10 } from "@kjgl77/datav-vue3";
</script>

<style lang="less" scoped>
.data_info {
  height: 100%;
  .info_box {
    display: flex;
    height: 100%;
    .need_people,
    .supply_people {
      width: 50%;
      height: 100%;
      padding-top: 5%;
      text-align: center;
      h1 {
        color: red;
      }
      span {
        font-size: 12px;
      }
    }
  }
}
</style>

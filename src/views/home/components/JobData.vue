<template>
  <chartCard title="柱状图-就业行业" :echartOption="echartOption" />
</template>

<script setup lang="ts">
import chartCard from "@/components/chartCard.vue";

// const props = defineProps<{}>();

const echartOption = {
  xAxis: [
    {
      data: ["前端", "后端", "金融", "美术", "教育", "摆摊"],
      axisLabel: {
        color: "#000",
      },
      axisLine: {
        lineStyle: {
          color: "#000",
        },
      },
    },
  ],
  yAxis: {
    axisLabel: {
      color: "#000",
    },
    axisLine: {
      show: true,
    },
  },
  series: [
    {
      name: "销量",
      type: "bar",
      data: [5, 20, 36, 10, 10, 0],
      itemStyle: {
        opacity: 1,
        color: "red",
      },
    },
  ],
};
</script>

<style></style>

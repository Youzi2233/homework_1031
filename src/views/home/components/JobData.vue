<template>
  <chartCard title="柱状图-就业行业" :echartOption="echartOption" />
</template>

<script setup lang="ts">
import chartCard from "@/components/chartCard.vue";

// const props = defineProps<{}>();

const echartOption = {
  xAxis: {
    data: ["前端", "后端", "金融", "美术", "教育", "摆摊"],
    series: [
      {
        name: "就业",
        type: "bar",
        data: [5, 20, 36, 10, 10, 20],
      },
    ],
  },
};
</script>

<style></style>

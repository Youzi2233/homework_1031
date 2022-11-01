<template>
  <chartCard title="柱状图-技能掌握" :echartOption="echartOption" />
</template>

<script setup lang="ts">
import chartCard from "@/components/chartCard.vue";

// const props = defineProps<{}>();

const echartOption = {
  dataset: {
    source: [
      ["score", "amount", "product"],
      [89.3, 58212, "Matcha"],
      [57.1, 78254, "Milk"],
      [74.4, 41032, "Cheese"],
      [50.1, 12755, "Cheese"],
      [89.7, 20145, "Matcha"],
      [68.1, 79146, "Tea"],
      [19.6, 91852, "Orange"],
      [10.6, 101852, "Lemon"],
      [32.7, 20112, "Walnut"],
    ],
  },
  grid: { containLabel: true },
  xAxis: { name: "amount" },
  yAxis: { type: "category" },
  visualMap: {
    orient: "horizontal",
    left: "center",
    min: 10,
    max: 100,
    text: ["High Score", "Low Score"],
    // Map the score column to color
    dimension: 0,
    inRange: {
      color: ["#65B581", "#FFCE34", "#FD665F"],
    },
  },
  series: [
    {
      type: "bar",
      encode: {
        // Map the "amount" column to X axis.
        x: "amount",
        // Map the "product" column to Y axis
        y: "product",
      },
    },
  ],
};
</script>

<style></style>

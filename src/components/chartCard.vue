<template>
  <div class="chart_card" :style="{ height: card_height }">
    <BorderBox10>
      <div class="card" style="height: 100%">
        <!-- 图表 -->
        <div ref="main" style="width: 100%; height: 100%"></div>
      </div>
    </BorderBox10>
  </div>
</template>

<script setup lang="ts">
import { BorderBox10 } from "@kjgl77/datav-vue3";
import echarts from "@/lib/echarts";
import { onMounted, ref, watchEffect } from "vue";
// 接收使用该组件时的参数，并设置默认值
const props = withDefaults(
  defineProps<{
    card_height?: string;
    title: string;
    title_color?: string;
    echartOption: echarts.EChartsCoreOption;
  }>(),
  {
    card_height: "300px",
    title_color: "#000",
  }
);

// 获取图表容器dom
const main = ref<HTMLElement>();
// 图表配置项
const echartOption = Object.assign(
  {
    title: {
      text: props.title,
      left: "center",
      textStyle: {
        color: "#000",
      },
    },
    legend: {
      top: "25",
    },
    tooltip: {},
    xAxis: [
      {
        data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
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
        data: [5, 20, 36, 10, 10, 20],
        itemStyle: {
          opacity: 1,
          color: "red",
        },
      },
    ],
  },
  props.echartOption
);

// 图表初始化
onMounted(() => {
  //   console.log(main.value);

  const mychart = echarts.init(main.value as HTMLElement);

  //   响应式的根据窗口宽度重置
  // window.onresize = function () {
  //   mychart.resize();
  // };
  // 上述方法，使用多个图表组件时只有一个生效
  window.addEventListener("resize", () => {
    mychart.resize();
  });
  watchEffect(() => {
    echartOption && mychart.setOption(echartOption);
  });
});
</script>

<style lang="less" scoped>
.chart_card {
  width: 100%;
  .card {
    padding: 10px;
    h1 {
      text-align: center;
      font-size: 18px;
    }
  }
}
</style>

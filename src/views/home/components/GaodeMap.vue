<template>
  <div id="container"></div>
</template>

<script setup lang="ts">
import AMapLoader from "@amap/amap-jsapi-loader";
import { shallowRef, onBeforeUnmount } from "vue";

const map = shallowRef<any>(null);

// 初始化地图
function initMap() {
  AMapLoader.load({
    key: "a9545972771d5b515d74e083753c1012", // 申请好的Web端开发者Key，首次调用 load 时必填
    version: "2.0", // 指定要加载的 JSAPI 的版本，缺省时默认为 1.4.15
    plugins: [""], // 需要使用的的插件列表，如比例尺'AMap.Scale'等
  })
    .then((AMap) => {
      map.value = new AMap.Map("container", {
        //设置地图容器id
        viewMode: "3D", //是否为3D地图模式
        zoom: 10, //初始化地图级别
        center: [119.974602, 31.814095], //初始化地图中心点位置
      });
      map.value.on("click", function (ev: any) {
        // 触发事件的对象
        var target = ev.target;
        // 触发事件的地理坐标，AMap.LngLat 类型
        var lnglat = ev.lnglat;
        // 触发事件的像素坐标，AMap.Pixel 类型
        var pixel = ev.pixel;
        // 触发事件类型
        var type = ev.type;
        console.log(target, lnglat, pixel, type);
      });
    })
    .catch((e) => {
      console.log(e);
    });
}

initMap();

onBeforeUnmount(() => {
  map.value && map.value.destroy();
});
</script>

<style lang="less" scoped>
#container {
  padding: 0px;
  margin: 0px;
  width: 100%;
  height: 100vh;
}
</style>

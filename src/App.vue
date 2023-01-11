<script setup>
import { ref, onMounted } from "vue";
import * as echarts from "echarts";

const refECharts = ref(null);
const randomSrc = ref("https://api.lorem.space/image/house");
const randomImg = () => {
  randomSrc.value = `https://api.lorem.space/image/house?w=${randomNumGen()}&h=${randomNumGen()}`;
};
const randomNumGen = () => parseInt(Math.random() * 500, 10);
const drawChart = () => {
  const myChart = echarts.init(refECharts.value);
  myChart.setOption({
    title: {
      text: "ECharts 入门示例",
    },
    tooltip: {},
    xAxis: {
      data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
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
};

onMounted(() => {
  drawChart();
});
</script>

<template>
  <div class="h-1/2 w-full flex flex-col">
    <div class="flex h-full b-1 b-solid b-blue w-full">
      <div class="w-32 bg-yellow p-4">some text</div>
      <div class="w-auto bg-red p-4">
        <img :src="randomSrc" alt="" class="max-h-100%" />
      </div>
      <div class="flex-1">
        <div class="w-full h-full" ref="refECharts"></div>
      </div>
    </div>
    <div><button @click="randomImg">change img</button></div>
  </div>
</template>

<style scoped></style>

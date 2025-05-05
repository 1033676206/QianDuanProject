<template>
  <div ref="pieChartRef" class="chart"></div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue';
import * as echarts from 'echarts';

const props = defineProps({
  data: {
    type: Object,
    required: true
  }
});

const pieChartRef = ref(null);
let pieChart = null;

onMounted(() => {
  initChart();
});

watch(
  () => props.data,
  () => {
    updateChart();
  },
  { deep: true }
);

const initChart = () => {
  pieChart = echarts.init(pieChartRef.value);
  updateChart();
};

const updateChart = () => {
  const option = {
    tooltip: {
      trigger: 'item',
      formatter: '{a} <br/>{b}: {c} ({d}%)'
    },
    legend: {
      orient: 'vertical',
      right: 10,
      top: 'center',
      textStyle: {
        color: '#fff'
      }
    },
    series: [
      {
        name: '分布',
        type: 'pie',
        radius: ['40%', '70%'],
        avoidLabelOverlap: false,
        label: {
          show: false,
          position: 'center'
        },
        emphasis: {
          label: {
            show: true,
            fontSize: '18',
            fontWeight: 'bold'
          }
        },
        labelLine: {
          show: false
        },
        data: props.data.datasets[0].data.map((value, index) => ({
          value: value,
          name: props.data.labels[index],
          itemStyle: {
            color: props.data.datasets[0].backgroundColor[index]
          }
        }))
      }
    ]
  };

  pieChart.setOption(option);
};

// 响应窗口大小变化
window.addEventListener('resize', () => {
  pieChart?.resize();
});
</script>

<style scoped>
.chart {
  width: 100%;
  height: 100%;
}
</style>
<template>
  <div ref="lineChartRef" class="chart"></div>
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

const lineChartRef = ref(null);
let lineChart = null;

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
  lineChart = echarts.init(lineChartRef.value);
  updateChart();
};

const updateChart = () => {
  const option = {
    tooltip: {
      trigger: 'axis',
      axisPointer: {
        type: 'shadow'
      }
    },
    grid: {
      left: '3%',
      right: '4%',
      bottom: '3%',
      top: '3%',
      containLabel: true
    },
    xAxis: {
      type: 'category',
      data: props.data.labels,
      axisLine: {
        lineStyle: {
          color: '#00c6ff'
        }
      },
      axisLabel: {
        color: '#fff'
      }
    },
    yAxis: {
      type: 'value',
      axisLine: {
        lineStyle: {
          color: '#00c6ff'
        }
      },
      axisLabel: {
        color: '#fff'
      },
      splitLine: {
        lineStyle: {
          color: 'rgba(0, 198, 255, 0.3)'
        }
      }
    },
    series: [
      {
        name: props.data.datasets[0].label,
        data: props.data.datasets[0].data,
        type: 'line',
        smooth: true,
        lineStyle: {
          width: 3,
          color: props.data.datasets[0].borderColor
        },
        areaStyle: {
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
            {
              offset: 0,
              color: props.data.datasets[0].borderColor.replace('0.5') 
            },
            {
              offset: 1,
              color: 'rgba(0, 198, 255, 0.05)'
            }
          ])
        },
        symbolSize: 8,
        itemStyle: {
          color: props.data.datasets[0].borderColor
        },
        areaStyle: {
          opacity: 0.3
        }
      }
    ]
  };

  lineChart.setOption(option);
};

// 响应窗口大小变化
window.addEventListener('resize', () => {
  lineChart?.resize();
});
</script>

<style scoped>
.chart {
  width: 100%;
  height: 100%;
}
</style>
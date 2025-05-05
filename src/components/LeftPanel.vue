<template>
    <div class="left-panel">
      <div class="panel-section">
        <h3>建成概况</h3>
        <div class="built-overview-cards">
          <div class="overview-card" v-for="(card, index) in overviewCards" :key="index">
            <div class="card-content">
              <div class="card-icon">
                <img :src="card.icon" :alt="card.title" />
              </div>
              <div class="card-text">
                <h4>{{ card.title }}</h4>
                <p>{{ card.value }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
  
      <div class="panel-section">
        <h3>农业产业分布情况</h3>
        <div class="chart-container">
          <pie-chart :data="pieChartData" />
        </div>
      </div>
  
      <div class="panel-section">
        <h3>粮食产量提升统计</h3>
        <div class="chart-container">
          <line-chart :data="lineChartData" />
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import PieChart from './charts/PieChart.vue';
  import LineChart from './charts/LineChart.vue';
  
  const overviewCards = [
    { title: "总建成项目", value: "2个", icon: "@/assets/folder.png" },
    { title: "高效节水规模", value: "600亩", icon: "@/assets/water.png" },
    { title: "新增建成项目", value: "2个", icon: "@/assets/new.png" },
    { title: "智慧农业面积", value: "600亩", icon: "@/assets/plant.png" },
    { title: "建成总规模", value: "2.06万亩", icon: "@/assets/rate.png" },
    { title: "新增粮食产量", value: "950吨/年", icon: "@/assets/grain.png" },
  ];
  
  const pieChartData = {
    labels: ['高效', '普通', '其他'],
    datasets: [
      {
        data: [30, 50, 20],
        backgroundColor: ['#00c6ff', '#00ffaf', '#99cc33'],
      },
    ],
  };
  
  const lineChartData = {
    labels: ['2020', '2021', '2022', '2023', '2024'],
    datasets: [
      {
        label: '粮食产量',
        data: [500, 650, 720, 850, 950],
        borderColor: '#00c6ff',
        backgroundColor: 'rgba(0, 198, 255, 0.1)',
        tension: 0.4,
      },
    ],
  };
  </script>
  
  <style>
  .left-panel {
    width: 200px;  /* 固定面板宽度 */
    height: 100%;
    padding: 10px;
    overflow-y: auto;
    background: rgba(0, 20, 50, 0.7);
    position: absolute;
    top: 0;
    z-index: 5; /* 确保面板在地图上层 */
  }
  
  .panel-section {
    margin-bottom: 10px;
  }
  
  h3 {
    font-size: 16px;
    margin-bottom: 10px;
    padding-bottom: 5px;
    border-bottom: 1px solid rgba(0, 150, 255, 0.3);
    color: #fff;
  }
  
  .built-overview-cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }
  
  .overview-card {
    background: rgba(0, 30, 80, 0.5);
    border: 1px solid rgba(0, 100, 255, 0.3);
    border-radius: 5px;
    padding: 10px;
    display: flex;
    align-items: center;
  }
  
  .card-content {
    display: flex;
    align-items: center;
  }
  
  .card-icon {
    width: 30px;
    height: 30px;
    background-color: rgba(0, 198, 255, 0.2);
    border-radius: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 10px;
  }
  
  .card-text h4 {
    margin: 0;
    font-size: 12px;
    color: #fff;
  }
  
  .card-text p {
    margin: 5px 0;
    font-size: 16px;
    color: #00c6ff;
    font-weight: bold;
  }
  
  .chart-container {
    height: 150px;
    background: rgba(0, 30, 80, 0.5);
    border: 1px solid rgba(0, 100, 255, 0.3);
    border-radius: 5px;
    padding: 10px;
  }
  </style>
  
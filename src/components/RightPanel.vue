<template>
    <div class="right-panel">
      <div class="panel-section">
        <h3>农业合作社/家庭农场</h3>
        <div class="farm-list">
          <div class="farm-item" v-for="(farm, index) in farms" :key="index">
            <div class="farm-info">
              <h4>{{ farm.name }}</h4>
              <p>承包地块: {{ farm.block }}</p>
              <p>经营期限: {{ farm.period }}</p>
            </div>
          </div>
        </div>
      </div>
  
      <div class="panel-section">
        <h3>农业企业</h3>
        <div class="enterprise-list">
          <div class="enterprise-item" v-for="(enterprise, index) in enterprises" :key="index">
            <div class="enterprise-info">
              <h4>{{ enterprise.name }}</h4>
              <p>主营行业: {{ enterprise.mainIndustry }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  const farms = [
    { name: '随县田丰农业种植有限公司-1', block: '新安街道片', period: '2022/04/20—2052/04/20' },
    { name: '随县田丰农业种植有限公司-2', block: '新安街道片', period: '2022/04/20—2052/04/20' },
  ];
  
  const enterprises = [
    { name: '随县田丰农业种植有限公司-1', mainIndustry: '蔬菜、水果种植与销售' },
    { name: '随县田丰农业种植有限公司-2', mainIndustry: '蔬菜、水果种植与销售' },
  ];
  </script>
  
  <style>
  .right-panel {
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
  
  .farm-list, .enterprise-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  
  .farm-item, .enterprise-item {
    background: rgba(0, 30, 80, 0.5);
    border: 1px solid rgba(0, 100, 255, 0.3);
    border-radius: 5px;
    padding: 10px;
  }
  
  .farm-info h4, .enterprise-info h4 {
    margin-top: 0;
    color: #00c6ff;
  }
  
  .farm-info p, .enterprise-info p {
    margin: 5px 0;
    font-size: 14px;
  }
  </style>
  
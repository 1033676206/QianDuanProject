<template>
    <header class="header">
      <h1 class="title">随州市数字化高标准农田大数据平台</h1>
      <div class="tabs">
        <button class="tab-btn active">建成综合一张图</button>
        <button class="tab-btn">建设规划一张图</button>
        <button class="tab-btn">智慧农业一张图</button>
        <button class="tab-btn">生产管理一张图</button>
        <button class="tab-btn">卫星遥感一张图</button>
      </div>
    </header>
  </template>
  
  <script setup>
  </script>
  
  <style scoped>
  .header {
    padding: 10px 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    background: rgba(0, 30, 80, 0.8);
    position: relative;
    z-index: 10;
  }
  
  .title {
    font-size: 24px;
    margin-bottom: 10px;
  }
  
  .tabs {
    display: flex;
    gap: 10px;
  }
  
  .tab-btn {
    background: rgba(0, 0, 0, 0.3);
    color: #fff;
    border: 1px solid #1a5fb4;
    padding: 8px 20px;
    border-radius: 20px;
    cursor: pointer;
    transition: background 0.3s;
  }
  
  .tab-btn.active {
    background: #1166cc;
    border-color: #1166cc;
  }
  
  .tab-btn:hover {
    background: rgba(0, 0, 0, 0.6);
  }
  </style>
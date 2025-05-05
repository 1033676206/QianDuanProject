<template>
    <header class="header">
      <div class="title-container">
        <h1 class="title">随州市数字化高标准农田大数据平台</h1>
      </div>
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
  
  <style>
  .header {
    background: #051830; /* 深色背景 */
    padding: 10px 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    z-index: 10; /* 确保在地图上层 */
  }
  
  .title-container {
    margin-bottom: 10px;
  }
  
  .title {
    font-size: 32px;
    font-weight: bold;
    color: #fff;
  }
  
  .tabs {
    display: flex;
    gap: 15px; /* 按钮之间的间距 */
  }
  
  .tab-btn {
    background: rgba(0, 0, 0, 0.3);
    color: #fff;
    border: 1px solid #1a5fb4;
    padding: 10px 20px;
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
  
<template>
  <div class="app-container">
    <!-- 地图作为全屏背景 -->
    <MapSection class="fullscreen-map" />
    
    <!-- 浮动在地图上的内容 -->
    <div class="overlay-content">
      <Header />
      <LeftPanel class="left-panel" />
      <RightPanel class="right-panel" />
      <FooterSection />
    </div>
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import LeftPanel from './components/LeftPanel.vue';
import MapSection from './components/MapSection.vue';
import RightPanel from './components/RightPanel.vue';
import FooterSection from './components/FooterSection.vue';
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body, html {
  width: 100%;
  height: 100%;
  font-family: 'Microsoft YaHei', sans-serif;
  background-color: #051830;
  color: #fff;
  overflow: hidden;
}

.app-container {
  width: 100vw;
  height: 100vh;
  position: relative;
  overflow: hidden;
}

/* 地图全屏 */
.fullscreen-map {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

/* 浮动内容 */
.overlay-content {
  position: relative;
  width: 100%;
  height: 100%;
  z-index: 2;
}

/* 头部样式调整 */
.header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 10;
}

/* 左侧面板样式调整 */
.left-panel {
  position: absolute;
  top: 80px; /* 头部高度 */
  left: 0;
  width: 200px;
  height: calc(100% - 120px); /* 减去头部和底部高度 */
  z-index: 5;
}

/* 右侧面板样式调整 */
.right-panel {
  position: absolute;
  top: 80px; /* 头部高度 */
  right: 0;
  width: 200px;
  height: calc(100% - 120px); /* 减去头部和底部高度 */
  z-index: 5;
}

/* 底部样式调整 */
.footer {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  z-index: 10;
}
</style>
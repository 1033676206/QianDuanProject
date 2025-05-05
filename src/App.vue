<template>
  <div class="app-container">
    <Header />
    <div class="main-content">
      <LeftPanel />
      <MapSection />
      <RightPanel />
    </div>
    <FooterSection />
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
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.main-content {
  display: flex;
  height: calc(100vh - 80px); /* 高度减去头部的高度 */
  position: relative;
  z-index: 1;
}

.left-panel, .right-panel {
  width: 200px;
  height: 100%;
  padding: 10px;
  overflow-y: auto;
  position: absolute;
  top: 0;
  z-index: 5;
}

.left-panel {
  border-right: 1px solid rgba(0, 100, 255, 0.2);
  left: 0;
}

.right-panel {
  border-left: 1px solid rgba(0, 100, 255, 0.2);
  right: 0;
}

.map-section {
  flex-grow: 1;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
}

footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  z-index: 10;
}
</style>

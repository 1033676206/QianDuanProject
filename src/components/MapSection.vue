<template>
    <div class="map-section">
      <div id="main-map" class="main-map"></div>
    </div>
  </template>
  
  <script setup>
  import { onMounted } from 'vue';
  import * as L from 'leaflet';
  
  onMounted(() => {
    const map = L.map('main-map').setView([31.7, 113.3], 8);
  
    L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
      attribution: 'Tiles © Esri',
    }).addTo(map);
  
    const projects = [
      { id: 'G13063323', name: '随县2024年新街镇片高标准农田建设项目', coordinates: [31.7, 113.3] },
      { id: 'G1309262300092001', name: '随县洪山片高标准农田建设项目', coordinates: [31.5, 113.5] },
    ];
  
    projects.forEach(project => {
      const marker = L.marker(project.coordinates).addTo(map);
      marker.bindPopup(`
        <div class="map-popup">
          <h4>编号: ${project.id}</h4>
          <p>项目名称: ${project.name}</p>
        </div>
      `).openPopup();
    });
  
    L.control.zoom({ position: 'topright' }).addTo(map);
  });
  </script>
  
  <style>
  .map-section {
    flex-grow: 1;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 0; /* 确保地图在底层 */
  }
  
  .main-map {
    width: 100%;
    height: 100%;
  }
  
  .map-popup {
    background: rgba(0, 30, 80, 0.8);
    border: 1px solid rgba(0, 100, 255, 0.5);
    color: white;
    border-radius: 5px;
    padding: 15px;
    width: 220px;
  }
  
  .map-popup h4 {
    margin-top: 0;
    color: #00c6ff;
  }
  
  .map-popup p {
    margin: 5px 0;
    font-size: 14px;
  }
  </style>
  
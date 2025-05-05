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
  
  <style scoped>
  .map-section, .main-map {
    width: 100%;
    height: 100%;
  }
  </style>
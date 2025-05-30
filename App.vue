<template>
  Inside App.vue, this text will not be visible if leaflet-toolbar is imported
   <div id="map" style="height: 500px; width: 100%;"></div>
</template>

<script setup lang="ts">
import L from "leaflet";
import 'leaflet-toolbar'; // this line breaks the build with rolldown-vite
import { onMounted, shallowRef } from 'vue';

const map = shallowRef<L.Map | null>(null);

onMounted(() => {
  map.value = L.map('map').setView([48.8566, 2.3522], 13);

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap contributors'
  }).addTo(map.value);
})
</script>

<style>
/* AI : Import Leaflet CSS for proper map styling */
@import 'leaflet/dist/leaflet.css';
</style>
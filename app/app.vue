<script setup lang="ts">
import { useMap } from "@indoorequal/vue-maplibre-gl"
import { MapLibreSearchControl } from "@stadiamaps/maplibre-search-box"
import "@stadiamaps/maplibre-search-box/dist/style.css"

const style = "https://tiles.stadiamaps.com/styles/alidade_satellite.json"

const mapContainer = useMap()
const control = new MapLibreSearchControl()

watch(() => mapContainer.isLoaded, (isLoaded) => {
  if (isLoaded)
    mapContainer.map!.addControl(control, "top-left")
})
</script>

<template>
  <div class="flex h-svh w-screen">
    <div id="actual-page">
      <MglMap
        :map-style="style"
        :center="[-13, 9]"
        :zoom="3"
      >
        <MglFullscreenControl />
        <MglNavigationControl />
        <MglGeolocateControl />
        <MglScaleControl />

        <MglMarker :coordinates="[-13.6, 9.6004923]" color="#cc0000" draggable>
          <mgl-popup>
            <h1 class="text-black">
              Hello
            </h1>
          </mgl-popup>
        </MglMarker>
      </MglMap>
    </div>
  </div>
</template>

<style>
#actual-page {
  width: 100%;
}

#actual-page > div {
  height: 100%;
}
</style>

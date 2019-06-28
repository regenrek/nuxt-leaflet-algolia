<template>
  <l-map
    class="min-h-screen z-10"
    :zoom="zoom"
    :center="center"
    :options="{ zoomControl: true }"
  >
    <l-tile-layer :url="url" />
    <div v-for="item in items" :key="item.id">
      {{ item }}
    </div>
    <div v-if="state">
      <l-marker
        v-for="item in state.items"
        :key="item.objectID"
        :lat-lng="item._geoloc"
      />
    </div>
  </l-map>
</template>
<script>
import { LMap, LTileLayer, LMarker } from "vue2-leaflet";
import { createWidgetMixin } from "vue-instantsearch";
import { connectGeoSearch } from "instantsearch.js/es/connectors";

export default {
  name: "MjMap",
  components: {
    LMap,
    LTileLayer,
    LMarker
  },
  mixins: [createWidgetMixin({ connector: connectGeoSearch })],
  data() {
    return {
      url: "http://{s}.tile.osm.org/{z}/{x}/{y}.png",
      zoom: 12,
      center: [47.5125, 16.03823]
    };
  }
};
</script>

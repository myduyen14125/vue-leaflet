<template>
  <div class="row map">
    <!-- {{brews}} -->
    <l-map @click="drawPolyline" :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <div v-for="marker in markers" :key="marker.id">
        <l-marker :lat-lng="marker">
          <l-popup>Hello! Bach Khoa here!</l-popup>
        </l-marker>
      </div>
      <l-polygon :lat-lngs="polygon.latlngs" :color="polygon.color"></l-polygon>
      <l-polyline
        :lat-lngs="polyline.latlngs"
        :color="polyline.color"
      ></l-polyline>
    </l-map>
  </div>
</template>
<script>
import L from "leaflet";
import { Icon } from "leaflet";
import {
  LMap,
  LTileLayer,
  LMarker,
  LPolygon,
  LPopup,
  LPolyline,
} from "vue2-leaflet";

delete Icon.Default.prototype._getIconUrl;
Icon.Default.mergeOptions({
  iconRetinaUrl: require("leaflet/dist/images/marker-icon-2x.png"),
  iconUrl: require("leaflet/dist/images/marker-icon.png"),
  shadowUrl: require("leaflet/dist/images/marker-shadow.png"),
});

export default {
  name: "MyAwesomeMap",
  props: {
    brews: Array,
  },
  components: {
    LMap,
    LTileLayer,
    LMarker,
    LPolygon,
    LPolyline,
    LPopup,
  },
  data: function () {
    return {
      zoom: 16,
      center: L.latLng(16.073202, -251.849894),
      url: "https://tile.thunderforest.com/cycle/{z}/{x}/{y}.png?apikey=028a5f1572504edb880aaf49dff433be",
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      currentZoom: 11.5,
      markers: [
        L.latLng(16.07557729489381, -251.84586204915567),
        L.latLng(16.07382916642506, -251.85017890497392),
        L.latLng(16.07482916642506, -251.85017890497392),
      ], //currentCenter
      polygon: {
        //insert node latlng here or get by click
        latlngs: [
          [16.073931386629923, -251.84963223491616],
          [16.074508600138373, -251.8480751600563],
          [16.073869542226063, -251.84783891421557],
          [16.0738901570295, -251.84773152974242],
          [16.072292503429004, -251.84707648445658],
          [16.072271888459976, -251.8469690999835],
          [16.07160190080265, -251.8468509770631],
          [16.07138544276942, -251.84644291606534],
          [16.07217534811412, -251.84454748198962],
          [16.072154733132955, -251.84450452820042],
          [16.07456667143015, -251.84510588124974],
          [16.075453102939544, -251.8452776964067],
          [16.07625707228621, -251.84557837293133],
          [16.07701980943035, -251.84607234150755],
          [16.0783597459759, -251.84684550971383],
          [16.0783597459759, -251.84686698660843],
          [16.078545274939618, -251.84701732487076],
          [16.078504046295983, -251.84718914002772],
          [16.078421588983037, -251.84718914002772],
          [16.078132988118465, -251.84772606239312],
          [16.077679471627622, -251.8483703692317],
          [16.07732902635787, -251.8486710457563],
          [16.07693735150182, -251.84903615296483],
          [16.076916737014336, -251.84927239880565],
          [16.07671059202192, -251.84937978327872],
          [16.075391259009002, -251.84886433780792],
          [16.074731589219482, -251.85000261322267],
          [16.074092532023865, -251.84972341359264],
        ],
        color: "red",
      },
      polyline: {
        latlngs: [
          [16.075216377590458, -251.8479629703841],
          [16.07647449348075, -251.84755509767876],
          [16.077175535989586, -251.8480509801678],
        ],
        color: "green",
      },
    };
  },
  methods: {
    latLng: function (lat, lng) {
      return L.latLng(lat, lng);
    },
    addMarker(event) {
      console.log(event.latlng);
      this.markers.push(event.latlng);
    },
    drawPolygon(event) {
      this.polygon.latlngs.push(event.latlng);
    },
    drawPolyline(event) {
      this.polyline.latlngs.push(event.latlng);
    }
  },
};
</script>
<style lang="scss" scoped>
.map {
  width: 60vw;
  height: 90vh;
}
</style>

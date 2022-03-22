<template>
  <div class="container">
    <div class="row">
      <div class="col-3">
        <List :brews="brews"></List>
      </div>
      <div class="col-9">
        <Map :brews="brews"></Map>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import List from './List.vue'
import Map from './Map.vue'
export default {
  name: 'Home',
  components: {List, Map},
  data: function () {
    return {
      brews: [],
    };
  },
  mounted: function () {
    axios.get("https://api.openbrewerydb.org/breweries").then((e) => {
      this.brews = e.data;
    });
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
h3 {
  margin: 40px 0 0;
}
a {
  color: #42b983;
}

</style>

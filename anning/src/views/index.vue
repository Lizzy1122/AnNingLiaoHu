<template>
  <div id="index_container">

    <div id="search_wrap">
      <search></search>
    </div>

    <div id="map_wrap">
    <map-contaciner></map-contaciner>
    </div>

  </div>
</template>

<script>
import MapContaciner from "@/components/MapContainer/MapContaciner.vue";
import Search from "@/components/Search/Search.vue";

export default {
  components: {Search, MapContaciner}

}
</script>

<style lang="less" scoped>
#index_container{
  height: 100%;
  width: 100%;
  position: relative;
  #map_wrap{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    height: 60%;
    width: 60%;
  }
  #search_wrap{
    position: absolute;
    top: 10%;
    left: 50%;
    height: 60px;
    width: 400px;
    transform: translate(-50%, -50%);

  }
}
</style>
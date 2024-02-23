<template>
  <div id="container">

  </div>
</template>

<script>
import AMapLoader from '@amap/amap-jsapi-loader'
import bus from '@/Bus/bus.js'
window._AMapSecurityConfig = {
  securityJsCode: 'cf8d45365c692d1d3ea73ed6285db429'
}
export default {
  data(){
    return {
      map:null,
      autoOptions: {
        input: ''
      },
      auto: null,

    }
  },
  methods:{
    initMap(){
      AMapLoader.load({
        key:"8eca6c8841a0a4a793f0c203442795b4",             // 申请好的Web端开发者Key，首次调用 load 时必填
        version:"2.0",      // 指定要加载的 JSAPI 的版本，缺省时默认为 1.4.15
        plugins:['AMap.ToolBar', 'AMap.Scale', 'AMap.HawkEye', 'AMap.MapType', 'AMap.Geolocation','AMap.AutoComplete'],       // 需要使用的的插件列表，如比例尺'AMap.Scale'等
      }).then((AMap)=>{
        this.map = new AMap.Map("container",{  //设置地图容器id
          viewMode:"3D",    //是否为3D地图模式
          zoom:10,           //初始化地图级别
          center:[121.473667, 31.230525], //初始化地图中心点位置
        })
        this.map.addControl(new AMap.Scale())
        this.map.addControl(new AMap.ToolBar())
        this.map.addControl(new AMap.HawkEye())
        this.map.addControl(new AMap.MapType())
        this.map.addControl(new AMap.Geolocation())

        this.auto = new AMap.AutoComplete(this.autoOptions)

      }).catch(e=>{
        console.log(e);
      })
    },
  },
  mounted() {
    //DOM初始化完成进行地图初始化
    this.initMap()
  },
  created() {
    bus.$on('shareUserInput',val=>{
      this.autoOptions.input=val.inputId
      console.log(val.inputId)
      console.log('autoOptions已经收到input')
    })
  }


}
</script>

<style lang="less" scoped>
#container {
  padding: 0px;
  margin: 0px;
  width: 100%;
  height: 100%;
}
</style>

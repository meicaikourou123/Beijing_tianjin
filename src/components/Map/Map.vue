<template>
    <div id="map"></div>
</template>
<script>
export default {
    data(){
        return {
            app:null,
            map:null,
            EVENT:null,//https://api.hifleet.com/nauticalmap/china/S101Chart/token?usertoken=v78RIz4+o2ING0QMIndN1Ya5uB09fRfVVnRjEjOYebf1/o/Qp4JB3FdOI/Ig+qTr&x={x}&y={y}&z={z}
            baseLayer:L.tileLayer('http://101.200.125.6:8234/nauticalmap/china/token?usertoken=v78RIz4+o2ING0QMIndN1Ya5uB09fRfVVnRjEjOYebf1/o/Qp4JB3FdOI/Ig+qTr&x={x}&y={y}&z={z}',{
                maxZoom:20,
                minZoom:1
            })
            //http://101.200.125.6:8234/nauticalmap/china/token?usertoken=？&x=？&y=？&z=？
            //http://m12.shipxy.com/tile.c?l=Na&m=o&x={x}&y={y}&z={z}
        }
    },
    // mixins:[mixin],
    mounted(){
      let _this = this
        setTimeout(function(){
          _this.initMap()
        },1000)
        
    },
    
    methods:{
        initMap(){  
            let _this = this
            function createMap (){
                _this.app = hifleet.create({ el: "map" })
                _this.map = _this.app.getMap()
                _this.EVENT = _this.app.EVENT
                _this.map.options.minZoom = 2
                _this.app.closeMap()
                _this.baseLayer.addTo(_this.map)
            }
            if(!this.app){
                createMap()
            }else{
                this.app && this.app.destory()
                createMap()
            }
            this.map.on(this.EVENT.HF_CLICK_ON_MAP, (a) => {
                console.log(a)
            })
        }
    }
}
</script>
<style >
#map{
    width: 100%;
    height: 100%;
}
</style>
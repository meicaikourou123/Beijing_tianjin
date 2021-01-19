<template>
    <div id="container">
        <Map class="entranceMap"/>
    </div>
</template>
<script>
import Map from './Map/Map'
// import{Button} from 'vant';
export default {
  data(){
    return {

    }
  },
  components:{
    Map
  }
}
</script>
<style lang="scss">
  #container{
    width:100%;
    height:100%;
  }
</style>
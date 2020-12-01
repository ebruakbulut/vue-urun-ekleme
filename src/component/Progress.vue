<template>
  <div class="progress">
    <div class="progress-bar bg-info" role="progressbar" :style="{width:progress +'%'}" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
      {{kayitsayisi}}/10
    </div>
  </div>
</template>
<script>
import {eventBus} from "../main";
export default {
  data(){
    return{
      kayitsayisi : 0,
      progress :0,
    }
  },
  created() {
    eventBus.$on("progressUpdate",(kayitsayisii)=>{
      this.kayitsayisi =kayitsayisii ;
      this.progress = kayitsayisii*10
    })
  },
}
</script>
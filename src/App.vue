<template>

<div class="container">
  <div class="row">
    <div class="col-md-12">
      <router-view></router-view>
    </div>
  </div>
</div> 


</template>

<script>
import Translate from "./components/Translate"

export default {
components:{
  Translate
}
  
}
</script>

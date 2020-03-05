<template>

<div class="container">
    <div class="row">
        <div class="col-md-12">
            <div class="panel panel-default">
                <div class="panel-body">
                    <h1 class="display-4">Arama geçmişiniz</h1>
                        <ul class="list-group">
                            <li  v-for="(value) in history" class="list-group-item">{{value}}</li>
                        </ul>
                </div>
            </div>
            
            
        </div>
    </div>
</div>

</template>

<script>
export default {

     data()
  {
      return{
         history : this.$store.state.history

      }
  }
  
}
</script>

<template>
<div class="container">
<form @submit.prevent="translate" class="well">
                <h1 class="display-4">Kelime Çevirici</h1>
                <textarea v-model="translateText" cols="30" rows="5" class="form-control" placeholder="Çevirmek istediğiniz kelime/cümle yazınız."></textarea>
                <br>
                <select v-model="word" class="form-control">
                    <option v-for="(value,key) in words" :value="key">{{value}}</option>
                </select>
                <br>
                <div class="text-left">
                    <strong>Seçilen kelime : {{words[word]}} </strong> 
                </div>
                <br>
                <button type="submit" class="btn btn-primary btn-block">Çevir!</button>
                <br>
                <span class="label label-success">Çeviriniz : {{result}}</span>
                
            </form>
            <button class="btn btn-primary btn-block" @click="navigate">Arama geçmişi</button>
            </div>
</template>

<script>
import axios from "axios";
export default {
  
  data()
  {
      return{
          translateText:'',
          word:'Seçildi',
          words:[],
          result:''

      }
  },
  methods : 
  {
      translate()
      {
          let url="https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20200305T094427Z.c58f77d5efc11cb9.1120fd8d4b3cdfe1d11ef6051238b5b04efa39d0&text="
          +this.words[this.word]+"&lang=tr"
          axios.get(url)
          .then(response =>{
              this.result=response.data.text[0];
              this.$store.state.history.push(this.words[this.word]);
              console.log(this.$store.state.history)

          }).catch(e => console.log(e))
          

      },
      navigate()
      {
          this.$router.push({name:'show'});
      }
  },
  watch : {
      translateText:function(value)
      {
          this.words=this.translateText.split(" ");
      }

  }


}
</script>
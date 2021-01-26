<template>

  <app-loader v-if="loading"></app-loader>

  <div class="card" v-if="comments.length !==0">
    <div >
      <h2>Комментарии</h2>
      <ul class="list" >
        <li class="list-item" v-for="(comment, i) in comments" :key="i">
          <div>
            <p><strong>{{comment.email}}</strong></p>
            <small>{{comment.body}}</small>
          </div>
        </li>
      </ul>
    </div>
  </div>

  <button class="btn primary" @click="fetchRequest" v-if="showButton">Загрузить комментарии</button>



</template>

<script>

import AppLoader from "@/AppLoader";
import axios from 'axios'

export default {
  emits:['activateLoader', 'shutLoader'],
  data(){
    return{
      comments:[],
      loading:false,
      showButton:true
    }
  },
  methods:{
    // getComments(){
    //
    //   this.fetchRequest()
    //
    // },
    async fetchRequest(){
      try {
          this.showButton=false
          this.loading=true
          const response = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
            this.comments=response.data
            console.log(response.data)
          this.loading=false
      } catch (e) {
        if (e){
          console.log(e)
          this.loading=false
        }
      }
    }

  },
  components:{AppLoader}
}
</script>

<style scoped>

</style>
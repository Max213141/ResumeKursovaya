<template>
  <div class="container column">
    <app-form
      @createResume="resumeHandler"

    ></app-form>
    <div class="card card-w70" id="#resume">
      <h3 v-if="resume.length===0">Добавьте первый блок, чтобы увидеть результат</h3>
      <div v-else
      >

        <component
          v-for="(part, i) in resume"
          :key="i"
          :is="part.titleOfElement"
          v-bind="{text:part.textOfElement}"
        ></component>
      </div>

    </div>
  </div>
  <div class="container">

    <app-comments></app-comments>

  </div>
</template>

<script>
import AppForm from "@/AppForm";
import AppTitle from "@/AppTitle";
import AppSubTitle from "@/AppSubTitle";
import AppAvatar from "@/AppAvatar";
import AppText from "@/AppText";
import AppComments from "@/AppComments";

export default {
  data(){
    return{
      hideAlert:false,
      resume:[],
      part:''
    }
  },
  methods:{
    resumeHandler(data){
      console.log(data)
      this.resume.push(data)
      console.log(this.resume)
    }
  },
  components:{
    AppForm,
    'app-title':AppTitle,
    'app-sub-title':AppSubTitle,
    'app-avatar':AppAvatar,
    'app-text':AppText,
    AppComments}
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>

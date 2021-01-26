<template>
  <div class="container column">
    <app-form
      @createResume="resumeHandler"

    ></app-form>
    <div class="card card-w70" id="#resume">
      <h3 v-if="resume.length===0">Добавьте первый блок, чтобы увидеть результат</h3>
      <div v-else v-for="(part, i) in resume" :key="i"
      >
        <component

          :is="part.titleOfElement"
          :data="part.textOffElement"
        ></component>
      </div>
<!--      <component :is="app-try" :></component>-->
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
      resume:[
        {
          titleOfElement:'app-title',
          textOffElement:'Suck my dick stupid bitch'
        },
        {
          titleOfElement:'app-text',
          textOffElement:'Suck my dick'
        },
        {
          titleOfElement:'app-avatar',
          textOffElement:'https://sun1.beltelecom-by-minsk.userapi.com/impg/2w6BvbSsBrlqunG9V4dx__xawryIEXP-c_yt8g/8p3yb1Dn474.jpg?size=200x0&quality=96&crop=3,3,748,748&sign=0806743d4d8c6898e916cf980fa29fbc&ava=1'
        }],
      part:''
    }
  },
  methods:{
    resumeHandler(data){
      console.log(data)
      this.resume=data
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

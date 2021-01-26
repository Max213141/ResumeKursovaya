<template>
    <form class="card card-w30">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="typeOfInput">
          <option value="app-title">Заголовок</option>
          <option value="app-sub-title">Подзаголовок</option>
          <option value="app-avatar">Аватар</option>
          <option value="app-text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" rows="3" v-model="textArea" placeholder="Введите текст"></textarea>
      </div>

      <button class="btn primary" :disabled="activateButton" @click.prevent="addElement"> Добавить</button>
    </form>
</template>

<script>
export default {
  emits:['createResume'],
  data(){
    return{
      typeOfInput: 'app-title',
      textArea: '',
      resumeParts: []
    }
  },
  methods:{
    addElement(){
      const resumePart={
        titleOfElement:this.typeOfInput,
        textOfElement:this.textArea
      }
      this.resumeParts.push(resumePart)
      const resumeParts=this.resumeParts
      this.$emit('createResume', resumeParts)
      this.typeOfInput='app-title'
      this.textArea=''
    }
  },
  computed:{
    activateButton(){
      if(this.textArea.length >= 3) {
        return false
      }
      return true
    },
  }
}
</script>

<style scoped>

</style>
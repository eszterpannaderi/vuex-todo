<template>
  <div class="form-floating">
      <input type="text"
       id="newtodo"
        class="form-control"
        v-model="newTodo"
        v-on:keyup.enter="saveTodo">
      <label for="newtodo">New ToDo</label>
  </div>
</template>

<script>
import store from '@/store'
export default {
    name:'todo-add-new',
    data(){
        return{
            newTodo:''
        }
    },
    methods:{
        saveTodo(){
            this.newTodo=this.newTodo.trim()
            if(this.newtodo=='')return
            store.commit('saveTodo',this.newTodo)
            this.newTodo=''

        }
    }

}
</script>

<style>

</style>
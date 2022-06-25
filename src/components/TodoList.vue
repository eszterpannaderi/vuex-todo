<template>
  <ul class="list-group">
      <li class="list-group-item"
          v-for="todo in $store.state.todos"
          :key="todo.id">
           <input 
           type="checkbox"
           id="todo.id"
           v-model="todo.completed" >

          <label class="ms-2"
                 v-if="!todo.isEdited"
                 @dblclick="editTodo(todo)"
                 :class="{'line-through': todo.completed}"
                 >{{todo.text}}</label>
          <input 
              type="text"
              :id="todo.id"
              class="form-control"
              v-model="todo.text"
              v-if="todo.isEdited"
              @keyup.enter="doneEdit(todo)"
              @keyup.esc="cancelEdit(todo)"
              @blur="canceledit(todo)"
              @vnode-mounted="({el})=>{el.focus()}"
                 >
                 <button @click="removeTodo" class="trash"><i class="bi bi-trash"></i></button>
           
          </li>
  </ul>
</template>

<script>
import store from '@/store'

//import store from '@/store'
export default {
    name:'todo-list',
//     computed:{
//         todos(){
//             return store.state.todos
//         }
//     }
date(){
  return{
    beforeEditText:null
  }
},
methods:{
  editTodo(todo){
    store.commit('editTodo',todo)

  },

  doneEdit(todo){
    this.beforeEditText=todo.text
    todo.text = todo.text.trim()
    if(todo.test=='')return
    store.commit('doneEdit', todo)
  },
  cancelEdit(todo){
    todo.text=this.beforeEditText
    store.commit('doneEdit', todo)


  },
  removeTodo(todo){
    store.commit('removeTodo',todo)
  }

}

}
</script>

<style>
.line-through{
  text-decoration:line-through;
}

.list-group-item .trash{
  display:none;
  background-color:transparent;
  border:none;
  position:absolute;
  right:10px;
  font-size:20px;

}
.list-group-item :hover .trash{
  display:inline-block;
}

.list-group-item .trash:hover{
  color:red;
}




</style>
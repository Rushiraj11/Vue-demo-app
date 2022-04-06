<template>
<div>
<div v-for="todo of todos " v-bind:key="todo.id">
  <!-- <div v-for="todo of completedTodos " v-bind:key="todo.id"> -->
    <TodoItemVue :todo="todo" @delete="deleteItem($event)">
    </TodoItemVue>
  </div>
  <button v-on:click="addTodo()" >Add todo</button>
  </div>
</template>

<script>import { computed } from "@vue/runtime-dom";
import TodoItemVue from "./TodoItem.vue";
//  import TodoItemVue from './TodoItem.vue';
// import TodoItem from './TodoItem.vue';


export default {

      data:function(){                                  // data is nothing but state in vue

     return{
           todos:[

               {
                  id:1,
                   title:'sample',
                   description:"Welcome to vue",
               },
               {
                  id:2,
                   title:'Message',
                   description:"Hello World",
                   completed:true
               }
           ],
     }
            
      },
    //   props:{                                  // used for communication from component to component like @input or @output in angular

    //  todo:Object,     }                  // always give type for props
           
   //  props:['todo','onClick']                               // props can be an array
           
    props:[],
    computed:{
   completedTodos(){
     return this.todos.filter(td=>td.completed);
   }
    },
    methods:{                                   // normal methods like "addTodo","delete","onsubmit","onClick"
            onTodoClick(){

            }, 
            addTodo(){
              this.todos.push({
                id:Math.random()*10,
                title:Math.random()*100,
              })
            },
            deleteItem(todo){
              this.todos= this.todos.filter(td=>td.id!=todo.id);
            }

    },
   mounted:function(){                          // lifecycle hook

   },
   destroyed:function(){                         // lifecycle hook

   },
   components:{
    TodoItemVue

}


}
</script>

<style>

</style>
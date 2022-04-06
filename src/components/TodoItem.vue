<template>
 <div class="container">
     {{todo.id}}
     {{todo.title}} 
     {{todo.description}} 
      <button @click="deleteitem()">Delete</button> 
 </div> 

</template>

<script>
export default {

        props:['todo'],
       methods:{
        deleteitem(){
            this.$emit('delete',this.todo)
        }
       }


}
</script>

<style>

</style>
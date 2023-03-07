<script setup>
import { ref, onMounted, computed, watch } from 'vue'

const todos=ref([])
const name=ref('')

const input_content=ref('')
const input_category=ref(null)

const todos_asc= computed(() => todos.value.sort((a,b)=>{
  return a.createdAt -b.createdAt 
} ))

watch(name,(newval) =>{
  localStorage.setItem('name',newval)
})
onMounted(()=>{name.value=localStorage.getItem('name')||''})

</script>

<template>
 <main class="app">

  <section class="greeting">
   <h2 class="title">
    whats up,<input type="text" placeholder="name here"
    v-model="name" />
   </h2> 
  </section>
  <section class="create-todo">
    <h3>Create a Todo</h3>
 <form @submit.prevent="addtTodo">
<h4>Whats on your Todo list?</h4>
<input 
type="text" 
placeholder="e.g make a example"
v-model= "input_content" />

<h4>pick a category</h4>
<div class="options">
  <label>
  <input 
  type="radio" 
  name="category" 
  id="category1"
  value="bussiness"
  v-model="input_category">
  <span class="bubble bussiness"></span>
  <div>Business</div>
</label>
<label>
  <input 
  type="radio" 
  name="category" 
  id="category1"
  value="bussiness"
  v-model="input_category">
  <span class="bubble bussiness"></span>
  <div>Business</div>
</label>
</div>
</form>

  </section>
 </main>


</template>


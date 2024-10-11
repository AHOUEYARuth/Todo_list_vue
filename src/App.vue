<template>
  <div class="todo">
    <form action="">
      <input type="text" v-model="myList" placeholder="saisir ici">
      <button @click="displayList">Ajouter</button>
    </form>
    <ul>
      <li v-for="(list, index) in lists" :key="index">
        <div @click="crossOutList($event)" class="around"></div>
        <span>{{ list }}</span>
      </li>
     <!--  <li v-for="list in lists">{{ list }}</li> -->
    </ul>
  </div>
</template>
<script setup lang="ts">
import {ref} from "vue";
const myList = ref('')
const lists = ref<string[]>([]);
function displayList(e: any) {
  e.preventDefault()
  /* lists.value.push(myList.value) */
  if (myList.value) {                
    lists.value.push(myList.value);
    myList.value = '';
  }
}
function crossOutList(event: any) {
  const listItem = event.target.nextElementSibling;
  listItem.classList.toggle('strike_through');
  
}

</script>

<style scoped>
  .todo{
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 30px;
  }
  form{
    width: 400px;
    display: flex;
    align-items: center;
    gap: 20px;
  }
  form input{
    width: 100%;
    padding: 10px;
    border: 1px solid grey;
    outline: none;
  }
  button{
    padding: 10px 15px;
    border: none;
    background-color: #1560BD;
    color: #fff;
    font-size: 18px;
    border-radius: 5px;
  }
  /* ul{
    display: flex;
    align-items: center;
    gap: 30px;
  } */
  ul li{
    list-style: none;
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 20px;
  }
  ul li .around{
    width: 15px;
    height: 15px;
    border: 1px solid grey;
    border-radius: 30px;
    background-color: inherit;
  }
  .strike_through {
    text-decoration: line-through;
    color: white;
  }
</style>

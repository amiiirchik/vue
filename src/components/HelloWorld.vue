<script setup>
import { computed, reactive, ref } from 'vue'


let elems = reactive(['Попить чай', 'Покодить', 'Написать диплом'])

  function filtered(){
    return elems
    //.filter(i => i % 2 === 0)
  }

  function addItem(inp){
    let input = ref(inp)
    elems.push(input._value)
  }

</script>

<template>
<div class="container pt-5" id="app2">
  <div class="card center form-control">
    <input v-model="inp" @keyup.enter="addItem(inp)">
    <button class="btn" @click="addItem(inp)">Добавить</button>
    <ul class="list" v-if="elems.length">
      <li class="list-item"
       @click="elems.splice(index, 1)"
       v-for="(elem, index) in filtered()"
       :key = elem
       >
       {{index}}
       
        <input id="itemInput" @click.stop :value="elem">
      </li>
    </ul>
    <p v-else>У вас нет текущих дел.</p>
  </div>
</div>

</template>

<style scoped lang="sass">
  #itemInput
    margin-left: 10px

  
</style>

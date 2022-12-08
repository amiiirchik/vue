<script setup>
import { computed, reactive } from 'vue'

defineProps({
  msg: String
})

let elems = reactive([1, 2, 3, 4, 5, 6])

computed(function filtered(elems){
  return this.elems.filter(i => i % 2 === 0)
}) 

</script>

<template>
<div class="container pt-5" id="app2">
  <div class="card center">
    <input @keyup.enter="addItem($event)">
    <button class="btn" @click="msg='Новое значение'">Добавить</button>
    <ul class="list" v-if="elems.length">
      <li class="list-item"
       @click="elems.splice(index, 1)"
       v-for="(elem, index) in filtered"
       :key = elem
       >
       index{{index}} - {{elem}}
       
        <input @click.stop>
      </li>
    </ul>
    <p v-else>Массив равен нулю</p>
  </div>
</div>

</template>

<style scoped lang="sass">

</style>

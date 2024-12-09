<script setup>
import {ref} from 'vue';
// variavel com tarefas
const tarefas = ref([
  "Entregar o desafio do starbucks", "Estudar vue.js" ,"Trabalhar" , "Comer batata e ovo", "Tomar pé treino e o whey", "Treinar"

])

// funçao para remover
function removerTarefa(index){
  tarefas.value.splice(index, 1)
}
// variavel para nova tarefa
// trim vai organizar o texto
const novaTarefa = ref("");

function adicionarTarefa(){
  if(novaTarefa.value.trim()!== ""){
    tarefas.value.push(novaTarefa.value.trim())
    novaTarefa.value= ""
  }
}

</script>

<template>
  <h1>📝Lista de tarefas</h1>
  <div v-if="tarefas.length=== 0">
    <p>Parabéns!! Você é o melhor de todos os tempos, uma máquina, uma besta enjaulada...</p>
  </div>

  <ul v-else>
    <!-- v-for é loop estamos usando para renderizar cada elemento -->
    <li v-for="(tarefa, index) in tarefas" :key="index"  >
      {{ tarefa }} <button @click="removerTarefa">❌​Remover</button></li>
  </ul>
  <section>
    <input type="text"
    placeholder="Digite sua nova tarefa"
    v-model="novaTarefa"
    >
    <button @click="adicionarTarefa">Add</button>
  </section>
</template>



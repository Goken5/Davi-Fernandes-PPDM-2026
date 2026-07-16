<script setup>
import { ref } from 'vue'
const lists = ref([{
  id: 1, nome: "Escola", newTask: "", tasks: [{
    id: Date.now(), text: "Atividade de Cesar", done: false
  }]
}])
const newListName = ref("")
const listsId = ref(1)

function addList() {
  const nome = newListName.value.trim();
  if (!nome) return;

  lists.value.push({id: Date.now(), nome, newTask: "", tasks: []})

}

function addTodo(listId) {
  const list = lists.value.find(
    list => list.id === listId
  )
  if (!list) return;
  const text = list.newTask.trim()
  if (!text) return;

  list.tasks.push({id: Date.now(), text, done: false})
  list.newTask = ""
}
newListName.value = "";

</script>

<template>
  <div>
    <input v-model="newListName" placeholder="Nova lista"/>
    <button @click="addList">Adicionar lista</button>

    <div v-for="list in lists" :key="list.id" class="list">
      <h2>{{list.nome}}</h2>
      <input v-model="list.newTask" placeholder="Nova tarefa"></input>
      <button @click="addTodo(list.id)">Adicionar tarefa</button>
    <ul>
      <li v-for="task in list.tasks" :key="list.id">{{task.text}}</li>
    </ul>
    </div>
  </div>
</template>
<template>
  <main>
    <!-- heading -->
    <header>
      <img src="./assets/img/pinia-logo.svg" alt="pinia logo">
      <h1>Pinia Tasks</h1>
    </header>
    <!-- new task form -->
    <div class="new-task-form">
      <TaskForm />
    </div>
    <!-- just for loading status -->
    <div class="loading" v-if="taskStore.loading">loading ...............</div>
    
    <!-- filter -->
    <div class="filter">
      <button @click="filter = 'all'">show all</button>
      <button @click="filter='favs'">show Favs</button>

      <!-- task lists -->
      <!-- All tasks -->
      <div class="task-list" v-if="filter==='all'">
        <p>you have {{ taskStore.totalCount }} tasks left to do</p>
        <div v-for="task in taskStore.tasks" :key="task.id">
          <TaskDetails :task="task"/>
        </div>
      </div>
      <!-- Favs -->
      <div class="task-list" v-if="filter === 'favs'">
        <p>you have {{ taskStore.favCount }} favs left to do</p>
        <div v-for="task in taskStore.favs" :key="task.id">
          <TaskDetails :task="task" />
        </div>
      </div>
    </div>
    </main>
</template>
<script setup>
  import {useTaskStore} from './Stores/TaskStore'

  const taskStore = useTaskStore()

  const filter = ref('all')

  taskStore.getTasks()
</script>
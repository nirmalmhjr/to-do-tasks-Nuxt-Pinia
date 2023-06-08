<template>
    <div class="task">
        <h3>{{ task.title }}</h3>
        <div class="icons">
            <i class="material-icons"
                @click="deleteTask(task.id)"
            >delete</i>
            <i class="material-icons"
            :class="{active: task.isFav}"
                @click="toggleFav(task.id)"
            >favorite</i>
        </div>
    </div>
</template>
<script setup>
import {useTaskStore} from '../Stores/TaskStore'
    defineProps({
        task:{
            type:Object,
            required:true
        }
    })
    
    const taskStore = useTaskStore()

   const {deleteTask, toggleFav} = taskStore
</script>
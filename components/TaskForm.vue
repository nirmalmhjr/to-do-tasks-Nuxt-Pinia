<template>
    <form @submit.prevent="handleSubmit">
        <input 
            type="text"
            placeholder="I need to..."
            v-model="newTask"
            
        >
        <button >Add</button>
    </form>
</template>
<script setup>
    import { useTaskStore } from '~/Stores/TaskStore';
    const newTask = ref('')

    const taskForce = useTaskStore()

    function handleSubmit() {
        if(newTask.value.length >0){
            taskForce.addTask({
                id:Math.floor(Math.random()*10000),
                title: newTask.value,
                isFav: false
            })
        }
    }
</script>
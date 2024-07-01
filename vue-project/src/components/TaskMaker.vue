<script setup>
import { ref, defineEmits } from 'vue';

const task = ref('');
const emit = defineEmits(['create-todo']);

function addTask() {
  if (task.value.length > 0) {
    emit('create-todo', task.value);
  }
  task.value = '';
}

</script>

<template>
    <div class="input-container">
        <input v-model="task" type="text" placeholder="do the groceries...">
        <button @click="addTask">Create</button>
    </div>
</template>

<style scoped>
    .input-container {
        border: 2px solid var(--secondary-color);
        border-radius: 7px;
    }

    input {
        padding: 10px;
        font-size: 20px;
        outline: none;
        border: none;
        border-radius: 7px;
    }

    button {
        padding: 10px;
        font-size: 20px;
        border: none;
        border-radius: 0 7px 7px 0;
        border-left: 2px solid var(--secondary-color) !important;
        cursor: pointer;
        background-color: #edebeb;
        transition: all .2s;
    }

    button:hover {
        background-color: #e4e2e2;
    }

    button:active {
        background-color: #edebeb;
    }


</style>
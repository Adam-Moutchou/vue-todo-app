<script setup>
import { ref } from 'vue';

import TaskMaker from '../components/TaskMaker.vue'

// const tasks = ref([]);

// function getTaskValue(data) {
//     tasks.value.push(data);
//     console.log(tasks.value) // For debugging
// }

const tasks = ref([]);

function getTaskValue(data) {
    const taskObj = {};
    taskObj.todo = data;
    taskObj.completed = false;
    tasks.value.push(taskObj);

    console.log(tasks.value) // For debugging
}

function getTodoStatus(event, index) {
    tasks.value[index].completed = event.target.checked;
    console.log(tasks.value) // For debugging
}
</script>

<template>
    <div class="todo-app">
        <div class="todo-app__input">
            <h2 class="todo-app__input-title">Write down your task</h2>
            <task-maker @create-todo="getTaskValue"/>
        </div>
        
        <div class="todo-app__list">
            <div id="todo-list" class="todo-list">
                <h2 class="todo-list__title">Tasks Todo:</h2>
                <div class="todo" v-for="(task, index) in tasks">
                    <div v-if="!task.completed">
                        <input type="checkbox" name="task-status" class="checkbox" :id="'checkbox-' + index" @change="getTodoStatus($event ,index)">
                        
                        <label :for="'checkbox-' + index">{{ task.todo }}</label>
                    </div>
                </div>
            </div>

            <div id="finished-tasks-list" class="todo-list">
                <h2 class="todo-list__title">Finished Tasks:</h2>
                <div class="todo" v-for="(task, index) in tasks">
                    <div v-if="task.completed">
                        <input type="checkbox" name="task-status" class="checkbox" :id="'checkbox-' + index" @change="getTodoStatus($event ,index)" checked>
                        
                        <label :for="'checkbox-' + index">{{ task.todo }}</label>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .todo-app {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 2rem;
        gap: 3rem;
    }

    .todo-app__input-title {
        text-align: center;
        font-size: 30px;
        margin-bottom: 1em;
    }

    .todo-app__list{
        display: flex;
        flex-direction: column;
        gap: 3rem;
        width: 70%;
        border-radius: 7px;
        padding: 20px;
        background-color: #fed9bc;
    }

    .todo-list {
        height: 25rem;
        overflow-y: auto;
        background-color: #fff;
        border-radius: 7px;
    }

    .todo-list .todo div {
        display: flex;
        align-items: center;
        gap: 20px;
        font-size: 25px;
        border-bottom: 2px solid var(--secondary-color);
        padding: 20px 20px 20px 40px;
    }

    .todo-list input[type="checkbox"] {
        accent-color: var(--secondary-color);
        width: 1.5rem;
        height: 1.5rem;
    }

    .todo-list .todo label {
        width: 100%;
        word-break: break-all;
    }

    .todo-list input[type="checkbox"]:checked + label {
        text-decoration: line-through;
        color: #6f6f6f;
    }

    .todo-list__title {
        padding: 20px;
        color: var(--secondary-color);
    }
</style>
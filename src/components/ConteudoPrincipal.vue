<script lang="ts">
import AddTask from './AddTask.vue';
import type ITask from '@/interfaces/ITask';
import Task from './Task.vue';


export default {
    data() {
        return {
            tasks: [] as ITask[]
        }
    },
    methods: {
        handleAddTask(task: ITask) {
            this.tasks.push(task)
        },
        handleDeleteTask(id: string) {
            this.tasks = this.tasks.filter((item) => item.id !== id)
        }
    },
    components: { AddTask, Task }
}
</script>

<template>
    <main class="container">
        <h1 class="text-center mt-4 fw-bold">Todo List</h1>
        <AddTask @adicionar-task="handleAddTask($event)" />
        <div>
            <ul v-if="tasks.length > 0" class="list-group mt-5 col-6">
                <h2 class="mt-4 mb-4">Tasks</h2>
                <Task v-for="task in tasks" :key="String(task.id)" :task="task"
                    @deletar-task="handleDeleteTask($event)" />
            </ul>
            <h2 class=" mt-4" v-else>Sem tasks para exibição</h2>
        </div>
    </main>
</template>
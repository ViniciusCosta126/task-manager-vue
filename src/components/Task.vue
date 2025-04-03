<script lang="ts">
import type ITask from '@/interfaces/ITask';
import type { PropType } from 'vue';

export default {
    props: {
        task: { type: Object as PropType<ITask>, required: true }
    },
    emits: ['deletarTask']
}
</script>


<template>
    <div class="list-group-item list-group-item-action" :class="[task.status === 'pendente' ? '' : 'text-bg-success']"
        aria-current="true">
        <div class="d-flex w-100 justify-content-between">
            <h5 class="mb-1">{{ task.titulo }}</h5>
            <div>
                <small>{{ new Date(task.dataCriacao).toLocaleDateString('pt-BR') }}</small>
                <small class="d-block fw-bold">{{ task.status.toUpperCase() }}</small>
            </div>

        </div>
        <p class="mb-1">{{ task.descricao }}</p>
        <div class="mt-2">
            <button class="btn btn-warning me-2">Editar</button>
            <button class="btn btn-danger" @click="$emit('deletarTask', task.id)">Excluir</button>
        </div>
    </div>
</template>
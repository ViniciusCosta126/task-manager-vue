<script lang="ts">
import type ITask from '@/interfaces/ITask';
import type { PropType } from 'vue';
import ModalEdicao from './ModalEdicao.vue';

export default {
    props: {
        task: { type: Object as PropType<ITask>, required: true }
    },
    emits: ['deletarTask'],
    components: { ModalEdicao }
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
            <button data-bs-toggle="modal" :data-bs-target="`#task-modal${task.id}`"
                class="btn btn-warning me-2">Editar</button>
            <button class="btn btn-danger" @click="$emit('deletarTask', task.id)">Excluir</button>
        </div>
    </div>
    <ModalEdicao :task="task" />
</template>
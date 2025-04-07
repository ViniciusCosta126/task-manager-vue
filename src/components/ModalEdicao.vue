<script lang="ts">
import type ITask from '@/interfaces/ITask';
import type { PropType } from 'vue';

export default {
    props: {
        task: { type: Object as PropType<ITask>, required: true }
    }
}
</script>

<template>
    <div class="modal fade" data-bs-backdrop="static" data-bs-keyboard="false" :id="`task-modal${task.id}`"
        tabindex="-1" :aria-labelledby="`task-modal${task.id}`" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered modal-lg">
            <div class="modal-content">
                <div class="modal-header">
                    <h1 class="modal-title fs-5" id="">{{ task.titulo }}</h1>
                </div>
                <div class="modal-body">

                    <div class="form-group mb-4">
                        <label class="" for="">Titulo</label>
                        <input class="form-control" type="text" v-model="task.titulo">
                    </div>
                    <div class="form-group mb-2">
                        <label class="" for="">Descricao</label>
                        <input class="form-control" type="text" v-model="task.descricao">
                    </div>

                    <div class="form-group mb-2">
                        <label class="" for="">Status</label>
                        <select class="form-select" v-model="task.status">
                            <option value="pendente">Pendente</option>
                            <option value="concluido">Concluído</option>
                        </select>
                    </div>

                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-primary" data-bs-dismiss="modal">Salvar</button>
                </div>
            </div>
        </div>
    </div>
</template>
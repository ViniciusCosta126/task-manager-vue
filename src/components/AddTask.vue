<script lang="ts">
export default {
    data() {
        return { tituloTask: '' as String, descricao: '' as String }
    },
    emits: ['adicionarTask'],
    methods: {
        criarTask() {
            if (this.tituloTask === '' || this.descricao === '') {
                alert('Existem campos vazios vazios.')
                return null
            }

            var task = {
                id: `${this.tituloTask.replace(' ', '')}${Math.floor(Math.random() * 1110000)}`,
                titulo: this.tituloTask,
                descricao: this.descricao,
                dataCriacao: new Date().toISOString(),
                status: 'pendente'
            }

            this.tituloTask = ''
            this.descricao = ''
            return task
        },
        adicionarTask() {
            const novaTask = this.criarTask()
            if (novaTask) {
                this.$emit('adicionarTask', novaTask)
            }
        }
    }
}
</script>

<template>
    <div class="mx-auto mt-4 row col-8 p-4 rounded shadow">
        <h2>Adicionar nova tarefa</h2>
        <div class="form-group mb-2">
            <label class="visually-hidden" for="">Titulo Task</label>
            <input class="form-control" v-model="tituloTask" type="text" placeholder="Digite a task para adicionar" />
        </div>
        <div class="form-group mb-2">
            <label class="visually-hidden" for="">Descricao</label>
            <input class="form-control" v-model="descricao" type="text" placeholder="Digite a descricao da tarefa" />
        </div>
        <div class="col-4">
            <button class="btn mt-0 btn-success" @click="adicionarTask">Adicionar task</button>
        </div>
    </div>
</template>
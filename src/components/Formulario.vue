<script setup>
		const propriedades = defineProps(['cadastrarTarefa', 'tarefaTemporaria', 'trocarFiltro', 'editaTarefaTemporaria'])
</script>

<template>
    <form @submit.prevent="propriedades.cadastrarTarefa">
        <div class="row">
            <div class="col">
                <input :value="propriedades.tarefaTemporaria" @change="propriedades.editaTarefaTemporaria" required type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control"/>
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select @change="propriedades.trocarFiltro" class="form-control">
                    <option value="todas">Todas tarefas</option>
                    <option value="todas">Pendentes</option>
                    <option value="todas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>
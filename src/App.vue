<script setup>
	import { reactive }	from 'vue';
	import Cabecalho from './components/Cabecalho.vue';
	import Formulario from './components/Formulario.vue';
	import Cadastrar from './components/Cadastrar.vue';

	const estado = reactive({
		filtro: 'todas',
		tarefaTemporaria:' ',
		tarefas:[
			{
				titulo: 'Estudar ES6',
				finalizada:false,
			},
			{
				titulo: 'Estudar SASS',
				finalizada:false,
			},
			{
				titulo: 'Ir para Academia',
				finalizada:true,
			},
		]
	})

	const getTarefasPendentes = () => {
		return estados.tarefas.filter(tarefas => tarefa.finalizada === false)
	}

	const getTarefasFinalizadas = () => {
		return estados.tarefas.filter(tarefas => tarefa.finalizada === true)
	}

	const getTarefasFiltradas = () => {
		const filtro = estado.filtro;
		switch (filtro) {
			case 'pendentes':
				return getTarefasPendentes();
			case 'finalizadas':
				return getTarefasFinalizadas();
			default:
				return estado.tarefas;
		}
	}

	const cadastrarTarefa = () => {
		const tarefaNova = {
			titulo: estado.tarefaTemporaria,
			finalizada: false,
		}
		estado.tarefas.push(tarefaNova);
		estado.tarefaTemporaria = ' ';
	}

</script>

<template>
		<Cabecalho :tarefas-pendentes="getTarefasPendentes().length"/>
		<Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :tarefa-temporaria="estado.tarefaTemporaria" :edita-tarefa-temporaria="evento => estado.tarefaTemporaria = evento.target.value" :cadastra-tarefa="cadastraTarefa"/>
		<Cadastrar :tarefas="getTarefasFiltradas()"/>
</template>

<style scoped>
</style>

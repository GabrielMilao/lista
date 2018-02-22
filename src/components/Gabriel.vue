<template>
	<div class="body">
		<section class="conteudoAlunos">
			<h1 class="titulo">Classificar</h1>
			<form>
				<div>
					<label>Ordenar por:</label>
					<select v-model="configs.orderBy">
						<option value="name">Nome</option>
						<option value="age">Idade</option>
					</select>
				</div><br>
				<div>
					<label>Ordem:</label>
					<select v-model="configs.order">
						<option value="asc">Crescente</option>
						<option value="desc">Decrescente</option>
					</select>
				</div><br>
				<div>
					<label>Filtrar</label>
					<input type="text" placeholder="Filtrar por nome" v-model="configs.filter">
				</div>
			</form>
		</section>
		<section class="conteudoAluno">
			<h1 class="titulo"> Alunos Vai na Web</h1>
			<ul>
				<li v-for="aluno in lista">
					{{aluno.name}}
					{{aluno.age}} anos
					<hr>
				</li>
			</ul>
		</section>
	</div>
</template>
<script>
	import _ from 'lodash'
	export default {
		name: 'Lista',
		data (){
			return{
				configs:{
					orderBy: 'age',
					order: 'asc',
					filter:''
				},
				alunos:[
					{
						name:'Gabriel Milão',
						age: '22'
					},
					{
						name:'Anna Luiza',
						age: '25'
					},
					{
						name:'Marco',
						age: '17'
					},
					{
						name:'Geraldo',
						age: '22'
					},
					{
						name:'Caio Gusmão',
						age: '17'
					},
					{
						name:'Rafael',
						age: '17'
					},
					{
						name:'Guilherme Maria',
						age: '17'
					},
					{
						name:'João Gabriel',
						age: '17'
					},

				]
			}
		},
	
	computed:{
		lista(){
			const filter = this.configs.filter;
			const lista = _.orderBy(this.alunos,this.configs.orderBy, this.configs.order);
			if (_.isEmpty(filter)) {
				return lista;
			}

			return _.filter(lista, aluno => aluno.name.index0f(filter) >=0);
		},
	}
}
</script>
<style scoped>
	.body{
		width: 100%;
		padding: 0;
		margin: 0;
		background: #696969;
		display: flex;
		justify-content: flex-start;
		align-items: center;
	}
	.conteudoAlunos{
		width: 50%;
	}
	li{
		list-style-type: none;
		color: #98FB98;
	}
	.titulo {
		color: #FFFAFA;

	}
</style>
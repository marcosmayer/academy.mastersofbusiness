<template>
	<div class="temas">
		<div class="temas__title">temas dos nossos cursos<span class="txtDarkGold">.</span></div>
		<div class="temas__grid-container">
			<BasicModule
				v-for="(module, index) in modules"
				:key="index"
				:title="module.title"
				:text="module.text"
			/>
		</div>
	</div>
</template>
<script>
import BasicModule from '../sections/BasicModule.vue'
export default {
	name: 'Temas',
	components: {
		BasicModule
	},
	data() {
		return {
			modules: [
				{
					title: 'Liderança',
					text: 'A arte de inspirar, motivar e orientar indivíduos, transformando seu potencial latente em realizações coletivas notáveis. A liderança é o catalisador que acelera o processo de transformar uma visão audaciosa em realidade tangível.'
				},
				{
					title: 'Gestão',
					text: 'A habilidade de organizar, planejar e controlar recursos de forma eficaz. É a ciência de garantir que todos os elementos de uma organização trabalhem harmoniosamente para atingir objetivos estratégicos.'
				},
				{
					title: 'Inovação',
					text: 'O ato contínuo de reinventar, criar e se adaptar. A inovação significa romper com o status quo, desafiar os limites do que é possível e introduzir novas formas de pensar e operar.'
				},
				{
					title: 'Marketing',
					text: 'A disciplina de entender e satisfazer as necessidades do cliente. Envolve a criação de conexões valiosas entre marcas e consumidores e a comunicação eficaz dos benefícios de produtos ou serviços.'
				},
				{
					title: 'Vendas',
					text: 'A arte de persuadir, negociar e satisfazer os clientes, convertendo oportunidades em resultados concretos. As vendas são o motor que alimenta a máquina de uma organização, permitindo que ela alcance e supere seus objetivos financeiros.'
				},
				{
					title: 'Estratégia',
					text: 'A capacidade de planejar e executar com visão. A estratégia envolve a navegação habilidosa no oceano de incertezas dos negócios, o desenvolvimento de planos de ação tangíveis e a reação proativa às mudanças do mercado.'
				}
			]
		}
	}
}
</script>
<style lang="sass" scoped>

.temas
	width: 100%
	height: auto
	background-color: $light-gold
	padding: 60px

	&__grid-container
		display: grid
		grid-template-columns: repeat(3, 1fr)
		grid-template-rows: repeat(2, auto)
		grid-row-gap: 80px
		grid-column-gap: 40px

	&__title
		font-family: 'npheavy', sans-serif
		text-align: center
		color: $darker-gold
		font-size: 4rem
		line-height: 4rem
		margin: 0 10% 40px
		text-transform: lowercase
		letter-spacing: 0.1em
</style>

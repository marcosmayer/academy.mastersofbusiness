<template>
	<div class="instrutores">
		<div class="instrutores__title">
			Conheça nossos Masters<span class="txtLightGold">.</span>
		</div>
		<div class="instrutores__grid-container">
			<Master
				v-for="(instrutor, index) in instrutores"
				:key="index"
				:name="instrutor.name"
				:description="instrutor.description"
				:image="instrutor.image"
			/>
		</div>
	</div>
</template>
<script>
import Master from '@/components/sections/Master.vue'
export default {
	name: 'Instrutores',
	components: {
		Master
	},
	data() {
		return {
			instrutores: [
				{
					name: 'Alberto Ferreira',
					description:
						'Alberto Ferreira foi Diretor Geral da Vivo Empresas, Presidente da SAP e fundador da Cervejaria Baden Baden.',
					image: '../../src/assets/images/alberto-ferreira.jpg'
				},
				{
					name: 'Carla Melhado',
					description: 'Presidente da Mutant',
					image: '../../src/assets/images/carla-melhado.jpg'
				},
				{
					name: 'Nicolas Fischer',
					description: 'Diretor geral no Brasil e Head para a América Latina da Coty',
					image: '../../src/assets/images/nicolas-fischer.jpg'
				},
				{
					name: 'Eduardo Gouveia',
					description: 'Conselheiro, Investidor em Startups e Consultor',
					image: '../../src/assets/images/eduardo-gouveia.jpg'
				},
				{
					name: 'David Carvalho',
					description: 'Chairman/CEO/President',
					image: '../../src/assets/images/david-carvalho.jpg'
				},
				{
					name: 'Marcos Mayer',
					description:
						'Marcos Mayer teve uma carreira dupla, dos dois lados da mesa: foi Diretor de Criação em agências e Diretor de Marketing em grandes empresas.',
					image: '../../src/assets/images/marcos-mayer.jpg'
				}
			]
		}
	}
}
</script>
<style lang="sass" scoped>
.instrutores
	width: 100%
	height: auto
	background-color: #0d0d0d
	padding: 60px

	&__grid-container
		display: grid
		grid-template-columns: repeat(2, 1fr)
		grid-template-rows: repeat(3, auto)
		grid-row-gap: 80px
		grid-column-gap: 40px

	&__title
		font-family: 'npheavy', sans-serif
		text-align: center
		color: $gold
		font-size: 4rem
		line-height: 4rem
		margin: 0 10% 40px
		text-transform: lowercase
		letter-spacing: 0.1em
</style>

<template>
	<div class="cursos">
		<div class="cursos__title">
			Temas relevantes, abordados por masters nos negócios<span class="txtLightGold">.</span>
		</div>
		<div class="cursos__grid-container">
			<div class="cursos__tema">Liderança</div>
			<div class="cursos__descricao">
				Como se tornar um líder que entrega resultados, com uma equipe de alta performance
			</div>
		</div>
		<div class="cursos__grid-container">
			<div class="cursos__tema">Inovação</div>
			<div class="cursos__descricao">
				A inovação gera riqueza e abre as portas para um crescimento sustentável
			</div>
		</div>
		<div class="cursos__grid-container">
			<div class="cursos__tema">Gestão</div>
			<div class="cursos__descricao">
				A gestão é o que faz tudo funcionar de forma sinérgica e dinâmica
			</div>
		</div>
		<div class="cursos__grid-container">
			<div class="cursos__tema">Marketing</div>
			<div class="cursos__descricao">
				A melhor estratégia é aquela que coloca o cliente no centro
			</div>
		</div>
		<div class="cursos__grid-container">
			<div class="cursos__tema">Vendas</div>
			<div class="cursos__descricao">
				Entregar valor para um cliente é a melhor forma de vender
			</div>
		</div>
	</div>
</template>
<script>
export default {
	name: 'Cursos'
}
</script>
<style lang="sass" scoped>
.cursos
	width: 100vw
	height: auto
	min-height: 300px
	background-color: $darker-gold
	padding: 60px

	&__title
		font-family: 'npheavy', sans-serif
		text-align: center
		color: $dark-gold
		font-size: 4rem
		line-height: 4rem
		margin-bottom: 60px
		text-transform: lowercase
		letter-spacing: 0.1em

	&__grid-container
		display: grid
		grid-template-columns: 1fr 5fr
		border: 1px solid $gold
		height: 80px
		border-radius: 40px
		margin-bottom: 60px

		&:last-child
			margin-bottom: 0

	&__tema
		color: $darker-gold
		font-size: 2rem
		line-height: 80px
		font-weight: 600
		text-align: center
		text-transform: uppercase
		background-color: $gold
		border-radius: 40px 0 0 40px
		font-weight: 700
		text-align: center

	&__descricao
		color: $gold
		font-size: 2rem
		line-height: 80px
		font-weight: 600
		text-align: center
		border-radius: 40px 0 0 40px
		text-align: left
		padding-left: 40px
</style>

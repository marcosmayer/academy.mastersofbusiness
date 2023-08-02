<template>
	<div class="experiencia">
		<div class="experiencia__title">
			Não é curso<span class="txtLightGold">.</span> É uma experiência de aprendizado<span
				class="txtLightGold"
				>.</span
			>
		</div>
		<div class="experiencia__grid-container">
			<div class="experiencia__module experiencia__module--1">
				<div class="experiencia__icp">Inspiração</div>
				<div class="experiencia__animal experiencia__dragon">
					<img src="@/assets/images/dragon.svg" alt="Inspiração" />
				</div>
				<div class="experiencia__simbolo experiencia__simbolo--dragon">
					O dragão é uma criatura majestosa e fascinante, que simboliza a ambição, a
					inovação e a busca pelo impossível. Ele nos inspira a enfrentar o desconhecido,
					sonhar grande e perseguir nossa visão com coragem e convicção.
				</div>
			</div>
			<div class="experiencia__module experiencia__module--2">
				<div class="experiencia__icp">Conhecimento</div>
				<div class="experiencia__animal experiencia__owl">
					<img src="@/assets/images/owl.svg" alt="Conhecimento" />
				</div>
				<div class="experiencia__simbolo experiencia__simbolo--owl">
					A coruja é um animal sagrado, venerado por sua sabedoria, e representa o
					conhecimento e o pensamento profundo. Ela nos convida a buscar a verdade, a
					aprender sempre e a iluminar a escuridão com o brilho do saber.
				</div>
			</div>
			<div class="experiencia__module experiencia__module--3">
				<div class="experiencia__icp">Prática</div>
				<div class="experiencia__animal experiencia__bull">
					<img src="@/assets/images/bull.svg" alt="Prática" />
				</div>
				<div class="experiencia__simbolo experiencia__simbolo--bull">
					O touro, um símbolo de força e determinação, representa a prática, a
					perseverança e a resiliência. Ele nos motiva a enfrentar desafios, a construir
					com nossas próprias mãos e a alcançar o sucesso através da dedicação e do
					trabalho árduo.
				</div>
			</div>
		</div>
		<div class="experiencia__sobre">
			Individualmente, cada um desses elementos - a inspiração, o conhecimento e a prática -
			tem um grande potencial de transformação. Mas, quando combinados de forma perfeita, eles
			se tornam uma força poderosa, capaz de gerar mudanças profundas e duradouras.
		</div>
	</div>
</template>
<script>
export default {
	name: 'Experiencia'
}
</script>
<style lang="sass" scope>
.experiencia
	width: 100vw
	height: auto
	min-height: 300px
	background-color: $gold
	padding: 60px 0 0

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
		grid-template-columns: repeat(3, minmax(0, 1fr))
		height: auto
		overflow: hidden

	&__module
		padding: 60px
		display: grid
		justify-items: center

	&__module--1, &__module--3
		background-color: $light-gold

	&__module--2
		background-color: $darker-gold

	&__icp
		font-family: 'npregular', sans-serif
		text-transform: uppercase
		text-align: center
		color: $gold
		font-size: 3rem
		margin-bottom: 60px
		letter-spacing: 0.1em

	&__animal
		width: auto
		max-width: 300px
		height: auto
		max-height: 300px
		margin-bottom: 60px

		img
			width: 100%
			height: 300px

	&__owl
		max-width: 400px

	&__simbolo
		text-align: center
		font-size: 1.5rem
		color: $darker-gold

	&__simbolo--owl
		color: $light-gold

	&__sobre
		width: 100%
		color: $light-gold
		background-color: $darker-gold
		font-size: 2rem
		text-align: center
		padding: 60px 15%
</style>

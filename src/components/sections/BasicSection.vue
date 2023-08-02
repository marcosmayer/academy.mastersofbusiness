<template>
	<section class="basic">
		<div class="basic__title">{{ title }}<span class="txtLightGold">.</span></div>
		<div class="basic__grid-container" :style="{ gridTemplateAreas: gridAreas }">
			<div class="basic__foto" :style="{ backgroundImage: `url(${image})` }"></div>
			<div class="basic__conteudo">
				<div class="basic__subtitle">{{ subtitle }}</div>
				<div class="basic__text" :style="{ lineHeight: lineHeight }">
					{{ text }}
				</div>
				<button class="basic__button">Quero saber mais</button>
			</div>
		</div>
	</section>
</template>
<script>
export default {
	name: 'BasicSection',
	props: {
		title: String,
		subtitle: String,
		text: String,
		image: String,
		gridAreas: String,
		lineHeight: String
	}
}
</script>
<style lang="sass" scoped>
.basic
	width: 100vw
	height: auto
	min-height: 300px
	background-color: #0d0d0d
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
		grid-template-columns: repeat(5, 1fr)
		grid-template-areas: "foto foto conteudo conteudo conteudo"
		height: 700px
		overflow: hidden

	&__foto
		grid-area: foto
		width: auto
		height: 100%
		background-color: $gold
		background-position: center
		background-size: cover

	&__conteudo
		grid-area: conteudo
		width: auto
		height: 100%
		padding: 0 15%
		text-align: left
		display: grid
		align-content: center

	&__subtitle
		width: 100%
		color: $gold
		font-size: 4rem
		font-family: 'npregular', sans-serif
		text-transform: uppercase
		text-align: left
		padding-bottom: 20px
		border-bottom: 5px solid $dark-gold
		margin-bottom: 40px

	&__text
		color: $gold
		font-size: 2rem
		text-align: left
		line-height: 4rem
		margin-bottom: 40px

	&__button
		width: 400px
		padding: 20px
		text-align: center
		color: $gold
		font-size: 2rem
		font-weight: 400
		cursor: pointer
		border: 2px solid $gold
		background-color: #0d0d0d

		&:hover
			color: #0d0d0d
			background-color: $gold
</style>

<template>
	<div class="module">
		<div class="module__title">{{ title }}</div>
		<div class="module__line"></div>
		<div class="module__text">
			{{ text }}
		</div>
	</div>
</template>
<script>
export default {
	name: 'BasicSection',
	props: {
		title: String,
		text: String
	}
}
</script>
<style lang="sass">
.module
	background-color: #fff
	box-shadow: 0 2px 6px rgba(0, 0, 0, 0.25)
	text-align: center
	padding: 40px

	&__title
		font-size: 2rem
		color: $dark-gold
		font-weight: 600

	&__line
		width: 100%
		height: 2px
		background-color: $gold
		margin: 20px 0

	&__text
		font-size: 1.5rem
		color: $gold
</style>

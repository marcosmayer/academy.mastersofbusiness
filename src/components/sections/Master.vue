<template>
	<div class="master">
		<div class="master__foto-area">
			<div class="master__foto" :style="{ 'background-image': `url(${image})` }"></div>
		</div>
		<div class="master__info">
			<div class="master__name">{{ name }}</div>
			<div class="master__line"></div>
			<div class="master__description">{{ description }}</div>
		</div>
	</div>
</template>
<script>
export default {
	name: 'Master',
	props: {
		name: String,
		description: String,
		image: String
	}
}
</script>
<style lang="sass" scoped>
.master
	background-color: $gold
	box-shadow: 0 2px 6px rgba(0, 0, 0, 0.25)
	padding: 60px
	@include dflex(space-between, center, row)

	&__foto-area
		width: 50%
		height: auto

	&__foto
		background-repeat: no-repeat
		background-position: center
		background-size: cover
		width: 320px
		height: 320px
		border-radius: 50%
		position: relative
		border: 2px solid $light-gold

		&::after
			content: ''
			position: absolute
			width: 340px
			height: 340px
			border-radius: 50%
			border: 2px solid $dark-gold
			left: -12px
			top: -12px

	&__info
		text-align: left
		width: 50%

	&__name
		font-size: 2rem
		color: $darker-gold
		font-weight: 700

	&__line
		width: 100%
		height: 2px
		background-color: $dark-gold
		margin: 20px 0

	&__description
		font-size: 1.4rem
		color: $darker-gold
</style>

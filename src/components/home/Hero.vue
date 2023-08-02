<template>
	<div class="hero">
		<Slider />

		<ApplicationLogo />

		<Menu />
	</div>
</template>

<script>
import ApplicationLogo from '../ApplicationLogo.vue'
import Menu from '../Menu.vue'
import Slider from '../home/Slider.vue'

export default {
	name: 'Hero',
	components: {
		Slider,
		ApplicationLogo,
		Menu
	}
}
</script>

<style lang="sass" scoped>
.hero
	width: 100vw
	height: 100vh
	overflow: hidden
	position: relative
</style>

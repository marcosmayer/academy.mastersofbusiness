<template>
	<div class="hero">
		<CursosSlider />

		<ApplicationLogo />

		<Menu />
	</div>
</template>

<script>
import ApplicationLogo from '@/components/ApplicationLogo.vue'
import Menu from '@/components/Menu.vue'
import CursosSlider from '@/components/cursos/CursosSlider.vue'

export default {
	name: 'Hero',
	components: {
		CursosSlider,
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

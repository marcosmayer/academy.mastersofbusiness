<template>
	<Hero />

	<KeySellingPoints />

	<Cursos />

	<Sobre />

	<Experiencia />

	<Incompany />

	<Footer />
</template>

<!-- SCRIPT -->

<script>
import ApplicationLogo from '@/components/ApplicationLogo.vue'
import Hero from '@/components/home/Hero.vue'
import KeySellingPoints from '@/components/home/KeySellingPoints.vue'
import Cursos from '@/components/home/Cursos.vue'
import Sobre from '@/components/home/Sobre.vue'
import Experiencia from '@/components/home/Experiencia.vue'
import Incompany from '@/components/home/Incompany.vue'
import Footer from '@/components/Footer.vue'

export default {
	components: {
		ApplicationLogo,
		Hero,
		KeySellingPoints,
		Cursos,
		Sobre,
		Experiencia,
		Incompany,
		Footer
	}
}
</script>

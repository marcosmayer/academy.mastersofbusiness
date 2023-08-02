<template>
	<CursosHero />

	<Temas />

	<Instrutores />

	<Footer />
</template>

<script>
import CursosHero from '@/components/cursos/CursosHero.vue'
import Temas from '@/components/cursos/Temas.vue'
import Instrutores from '@/components/cursos/Instrutores.vue'
import Footer from '@/components/Footer.vue'
export default {
	components: {
		CursosHero,
		Temas,
		Instrutores,
		Footer
	}
}
</script>

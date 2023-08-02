<template>
	<BasicSection
		title="Quem é a Masters of Business"
		subtitle="Sobre nós"
		text="A Masters of Business é uma escola de negócios que nasceu do desejo de compartilhar o que aprendemos durante décadas atuando como executivos e empreendedores de sucesso."
		image="../../src/assets/images/partners.jpg"
		gridAreas="'foto foto conteudo conteudo conteudo'"
	/>
</template>
<script>
import BasicSection from '@/components/sections/BasicSection.vue'
export default {
	name: 'Sobre',
	components: {
		BasicSection
	}
}
</script>
<style lang="sass" scoped></style>

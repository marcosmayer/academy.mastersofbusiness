<template>
	<div class="ksp">
		<div class="ksp__title">
			Vamos mudar a forma como o conhecimento de negócios é compartilhado<span
				class="txtDarkGold"
				>.</span
			>
		</div>
		<div class="ksp__grid-container">
			<div class="ksp__grid-item reveal" style="transition-delay: 0s">
				<div class="ksp__item-destaque">Origem</div>
				<div class="ksp__item-title">
					Uma escola criada por executivos e empreendedores, para executivos e
					empreendedores
				</div>
				<div class="ksp__item-text">
					A escola nasceu do nosso desejo de compartilhar o que aprendemos durante décadas
					atuando como executivos e empreendedores de sucesso.
				</div>
			</div>
			<div class="ksp__grid-item reveal" style="transition-delay: 0.25s">
				<div class="ksp__item-destaque">Metodologia</div>
				<div class="ksp__item-title">
					Oferecemos a melhor experiência de aprendizado, com a aplicação perfeita da
					metodologia ICP
				</div>
				<div class="ksp__item-text">
					O aprendizado acontece de forma efetiva, por meio da combinação perfeita entre
					inspiração, conhecimento e prática.
				</div>
			</div>
			<div class="ksp__grid-item reveal" style="transition-delay: 0.5s">
				<div class="ksp__item-destaque">Cohort</div>
				<div class="ksp__item-title">
					Cohort-Based Learning: o primeiro formato de cursos online nativo da Internet
				</div>
				<div class="ksp__item-text">
					As primeiras ondas de educação digital foram adaptações do mundo físico para o
					online. O Cohort-Based Learning nasceu para mudar isso.
				</div>
			</div>
			<div class="ksp__grid-item reveal" style="transition-delay: 0s">
				<div class="ksp__item-destaque">Inovação</div>
				<div class="ksp__item-title">
					Plataforma de ensino própria e ambiente de simulação (business game), para
					garantir o aprendizado
				</div>
				<div class="ksp__item-text">
					Para suportar nossa metodologia de ensino, desenvolvemos nossa própria
					plataforma de ensino e um ambiente de simulação.
				</div>
			</div>
			<div class="ksp__grid-item reveal" style="transition-delay: 0.25s">
				<div class="ksp__item-destaque">Não é um MBA</div>
				<div class="ksp__item-title">
					O aprendizado efetivo não precisa de um altíssimo compromisso financeiro e do
					seu tempo
				</div>
				<div class="ksp__item-text">
					É possível aprender um tema com profundidade em algumas semanas, e sem gastar
					uma fortuna.
				</div>
			</div>
			<div class="ksp__grid-item reveal" style="transition-delay: 0.5s">
				<div class="ksp__item-destaque">Masters</div>
				<div class="ksp__item-title">
					Nossos instrutores são executivos e empresários de ponta, que sabem fazer o que
					ensinam
				</div>
				<div class="ksp__item-text">
					Nossos Masters são executivos e empresários de alto nível, que ensinam aquilo
					que aprenderam na prática.
				</div>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	name: 'KeySellingPoints',

	mounted() {
		// Attach event listener when the component is mounted
		window.addEventListener('scroll', this.reveal)
	},
	beforeDestroy() {
		// Cleanup - remove the event listener when the component is about to be destroyed
		window.removeEventListener('scroll', this.reveal)
	},
	methods: {
		reveal() {
			var reveals = document.querySelectorAll('.reveal')

			for (var i = 0; i < reveals.length; i++) {
				var windowHeight = window.innerHeight
				var elementTop = reveals[i].getBoundingClientRect().top
				var elementVisible = 50

				if (elementTop < windowHeight - elementVisible) {
					reveals[i].classList.add('active')
				} else {
					reveals[i].classList.remove('active')
				}
			}
		}
	}
}
</script>
<style lang="sass" scoped>
.ksp
	width: 100%
	height: auto
	background-color: $light-gold
	padding: 60px

	&__title
		font-family: 'npheavy', sans-serif
		text-align: center
		color: $darker-gold
		font-size: 4rem
		line-height: 4rem
		margin-bottom: 100px
		margin: 0 10% 100px
		text-transform: lowercase
		letter-spacing: 0.1em

	&__grid-container
		display: grid
		grid-template-columns: repeat(3, 1fr)
		grid-template-rows: repeat(2, auto)
		grid-template-areas: "ksp1 ksp2 ksp3" "ksp4 ksp5 ksp6"
		grid-row-gap: 80px
		grid-column-gap: 40px

	&__grid-item
		background-color: $darker-gold
		padding: 40px
		height: auto
		box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23)
		position: relative

	&__item-destaque
		position: absolute
		color: $darker-gold
		font-size: 3rem
		font-family: 'npheavy', sans-serif
		text-transform: uppercase
		text-align: right
		right: 0
		top: -53px

	&__item-title
		color: $light-gold
		font-size: 1.75rem
		text-align: left
		font-weight: 700
		padding-bottom: 20px
		border-bottom: 2px solid $dark-gold
		margin-bottom: 20px

	&__item-text
		color: $dark-gold
		font-size: 1.5rem
		text-align: left
		font-weight: 600

.reveal
	position: relative
	transform: translateY(100px)
	opacity: 0
	transition: 2s all ease

.reveal.active
	transform: translateY(0)
	opacity: 1
</style>

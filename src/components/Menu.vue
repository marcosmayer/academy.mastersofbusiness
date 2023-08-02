<template>
	<div
		class="hero__menu"
		v-bind:style="{
			'background-color': isOpen ? 'rgba(25, 22, 19, 0)' : 'rgba(25, 22, 19, 1)'
		}"
	>
		<div class="hero__hamburguer" v-show="!isOpen" @click="isOpen = true">
			<span class="material-symbols-outlined icon-open"> menu </span>
		</div>
		<transition name="fade">
			<div
				class="hero__hamburguer--close"
				v-if="isOpen"
				v-bind:style="{
					backgroundColor: isOpen ? 'rgba(164, 152, 122, 1)' : 'rgba(164, 152, 122, 0)'
				}"
				@click="isOpen = false"
			>
				<span class="material-symbols-outlined icon-close"> close </span>
			</div>
		</transition>
		<div class="hero__icons">
			<span class="material-symbols-outlined icon-user"> person </span>
			<span class="material-symbols-outlined icon-search"> search </span>
		</div>
		<div class="hero__cta">
			<div class="hero__cta-content">
				<div class="hero__cta-text">Quero me inscrever</div>
				<div class="hero__cta-icon">
					<span class="material-symbols-outlined icon-arrow"> chevron_right </span>
				</div>
			</div>
		</div>
	</div>
	<div
		class="hero__menu--open"
		v-bind:style="{
			transform: isOpen ? 'translateX(0)' : 'translateX(100%)',
			opacity: isOpen ? 1 : 0
		}"
	>
		<div class="hero__menu-area">
			<RouterLink class="hero__menu-item" to="/"><div>Início</div></RouterLink>
			<RouterLink class="hero__menu-item" to="/cursos"><div>Cursos</div></RouterLink>
			<div class="hero__menu-item">Para empresas</div>
			<div class="hero__menu-item">Sobre</div>
			<div class="hero__menu-item">Contato</div>
		</div>
	</div>
</template>
<script>
export default {
	name: 'Menu',
	components: {},

	data() {
		return {
			isOpen: false
		}
	}
}
</script>
<style lang="sass" scoped>
.hero

	&__menu
		width: 180px
		height: 100vh
		position: absolute
		right: 0
		background-color: rgba(25, 22, 19, .8)
		display: grid
		grid-template-columns: 180px
		grid-template-rows: 180px auto 300px
		grid-template-areas: "menu-icon" "center-icons" "cta"
		place-items: center
		top: 0
		z-index: 9
		transition: background-color 0.5s ease

	&__hamburguer
		grid-area: menu-icon
		cursor: pointer
		display: grid
		place-content: center
		width: 180px
		height: 180px
		background-color: rgba(164, 152, 122, 0)

	&__hamburguer--close
		grid-area: menu-icon
		cursor: pointer
		background-color: rgba(164, 152, 122, 1)
		width: 180px
		height: 180px
		display: grid
		place-content: center
		transition: background-color 0.5s ease

	&__icons
		grid-area: center-icons
		display: flex
		flex-direction: column

	&__cta
		grid-area: cta
		color: $gold
		text-transform: uppercase
		font-size: 1.75rem
		width: 100%
		height: 100%
		display: grid
		place-items: center
		font-weight: 600

	&__cta-content
		position: absolute
		width: 360px
		height: 60px
		line-height: 60px
		transform: rotate(270deg)
		bottom: 180px
		display: flex
		padding-left: 20px
		cursor: pointer

		&:hover, &:hover .icon-arrow
			color: $dark-gold
			background-color: $gold

	&__cta-icon
		margin-top: 7px

	&__menu--open
		width: 620px
		height: 100vh
		position: absolute
		right: 0px
		bottom: 0
		background-color: rgba(0, 0, 0, .8)
		background-image: url("../assets/images/noise-bg.png")
		backdrop-filter: blur(20px)
		padding: 120px 270px 120px 90px
		transform: translateX(440px)
		opacity: 0
		transition: transform 0.5s ease, opacity 0.5s ease
		z-index: 8

	&__menu-area
		width: 100%
		height: 100%
		z-index: 10
		@include dflex(center, center, column)

	&__menu-item
		width: 100%
		height: 50px
		line-height: 50px
		text-align: center
		color: $gold
		font-size: 1.25rem
		font-weight: 600
		margin-bottom: 50px
		cursor: pointer
		padding-bottom: 7px
		border-bottom: 1px solid $gold

		&:last-child
			margin-bottom: 0

		&:hover
			color: $gold
			background-color: $darker-gold
			text-decoration: none

.icon-user
	font-size: 36px
	margin-bottom: 10px
	color: $gold

.icon-search
	font-size: 36px
	color: $gold

.icon-arrow
	display: inline-block
	color: $gold
	font-size: 48px

.icon-open, .icon-close
	transition: opacity 0.5s ease
	opacity: 0

.icon-open
	color: $gold
	font-size: 48px
	opacity: 1

.icon-close
	color: $dark-gold
	font-size: 60px
	opacity: 1

.fade-enter-active, .fade-leave-active
	transition: opacity 0.5s

.fade-enter, .fade-leave-to
	transition: opacity 0.5s
	opacity: 0
</style>

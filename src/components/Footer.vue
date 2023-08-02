<template lang="">
	<footer class="footer">
		<div class="footer__logo">
			<img
				src="@/assets/images/logo-masters-of-business.svg"
				alt="Logo Masters of Business"
			/>
		</div>
		<div class="footer__copyright">
			Copyright © {{ currentYear }}, Masters of Business. Todos os direitos reservados.
		</div>
	</footer>
</template>
<script>
export default {
	name: 'Footer',
	computed: {
		currentYear() {
			return new Date().getFullYear()
		}
	}
}
</script>
<style lang="sass" scoped>
.footer
	width: 100vw
	height: auto
	color: $light-gold
	background-color: $dark-gold
	font-size: 1.5rem
	text-align: center
	padding: 40px 0

	&__logo
		width: 100%
		height: auto
		display: grid
		place-content: center
		margin-bottom: 60px

		img
			width: 400px
			height: auto

	&__privacy
		width: 50%
		padding: 0 40px 0 0
		text-align: right

		& a
			text-decoration: none
			color: $dark-gold

		& a:hover
			text-decoration: underline
			color: $light-gold
</style>

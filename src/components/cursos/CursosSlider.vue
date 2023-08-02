<!--
//	* Comentário
//	! Comentário
//	? Comentário
//	& Comentário
//	^ Comentário
//	~ Comentário
//	todo Comentário
//	// Comentário
-->

<template>
	<div class="slider" ref="sliderRef">
		<div
			class="slider__box"
			v-for="(slide, index) in slides"
			:key="index"
			:class="{ 'is-video': slide.isVideo }"
			:style="slide.isVideo ? {} : { backgroundImage: `url(${slide.backgroundImage})` }"
		>
			<div v-if="slide.isVideo" class="slider__video-wrapper">
				<video class="slider__video" autoplay muted loop :src="slide.videoLink"></video>
			</div>
			<div class="slider__destaque">
				<span v-html="slide.title"></span>
			</div>
			<div class="slider__text">
				{{ slide.description }}
			</div>
			<div class="slider__darken"></div>
			<div class="slider__pattern"></div>
		</div>
	</div>
	<div class="progress-bar--bg"></div>
	<div class="slider__bottom"></div>
	<div
		class="progress-bar"
		ref="progressBarRef"
		v-bind:style="{ height: progressBar + '%' }"
	></div>
	<div class="controls">
		<button class="controls__button" data-index="0" @click="changeSlide(0)"></button>
		<button class="controls__button" data-index="1" @click="changeSlide(1)"></button>
		<button class="controls__button" data-index="2" @click="changeSlide(2)"></button>
		<button class="controls__button--pause" @click="pauseSlider">
			<span class="material-symbols-outlined icon-pause" v-if="isPlaying">pause_circle</span>
			<span class="material-symbols-outlined icon-play" v-else>play_circle</span>
		</button>
	</div>
	<div class="scroll"></div>
</template>
<script>
import { ref, onMounted, onUnmounted, watch, computed } from 'vue'
export default {
	name: 'Slider',
	data() {
		return {
			progressBar: null,
			isPlaying: true,
			currentSlide: 0
		}
	},
	setup() {
		const slides = [
			{
				title: 'Olhe para cima. É lá que o seu futuro está.',
				description:
					'Não se trata de acumular certificados. Se trata de descobrir como ser sempre melhor.',
				isVideo: true,
				videoLink: '../../src/assets/images/eyes.mp4'
			},
			{
				title: 'Liderança de alta performance',
				description: 'Juntos, corações e mentes, com um único objetivo.',
				backgroundImage: '../../src/assets/images/bg-performance.jpg'
			},
			{
				title: 'O que você <span style="text-decoration: line-through; opacity: 0.5">quer</span> <span style="font-family: npheavy; text-decoration: underline">precisa</span> aprender hoje?',
				description:
					'Você aprende aquilo que precisa, para poder aplicar imediatamente no seu trabalho.',
				backgroundImage: '../../src/assets/images/bg-precisa.jpg'
			}
		]

		const isPlaying = ref(true)
		const currentSlide = ref(-1)
		const sliderRef = ref(null)
		const progressBarRef = ref()
		const slideCount = computed(() => slides.length)
		let intervalId

		// & Inicia a transição de slides e reseta a barra de progresso
		onMounted(() => {
			startSlider(currentSlide)
			document
				.querySelector('.controls__button[data-index="0"]')
				.classList.add('controls__button--selected')
			restartProgressBarAnimation()
		})
		// & Inicia o slider, chama a função que altera o slide a cada 7 segundos, reseta a barra de progresso e muda o botão de seleção de slide
		const startSlider = () => {
			// Move to the next slide immediately when the slider starts
			currentSlide.value = (currentSlide.value + 1) % slideCount.value

			// Restart the progress bar animation
			restartProgressBarAnimation()

			// Change the selected control button
			document.querySelectorAll('.controls__button').forEach((button) => {
				button.classList.remove('controls__button--selected')
			})
			document
				.querySelector(`.controls__button[data-index="${currentSlide.value}"]`)
				.classList.add('controls__button--selected')

			// Start the interval for automatic slide transition
			intervalId = setInterval(() => {
				currentSlide.value = (currentSlide.value + 1) % slideCount.value

				restartProgressBarAnimation()

				document.querySelectorAll('.controls__button').forEach((button) => {
					button.classList.remove('controls__button--selected')
				})
				document
					.querySelector(`.controls__button[data-index="${currentSlide.value}"]`)
					.classList.add('controls__button--selected')
			}, 7000)
		}

		// & Reseta e reinicia a animação da barra de progresso
		const restartProgressBarAnimation = () => {
			let progressBar = progressBarRef.value
			progressBar.style.animation = 'none'
			progressBar.offsetHeight
			progressBar.style.animation = ''
		}

		// & Função chamada quando um botão de seleção de slide é clicado
		// & Para a transição do slide atual, segue para o slide selecionado e reseta a barra de progresso
		const changeSlide = (slideIndex) => {
			stopSlider()
			currentSlide.value = slideIndex - 1
			startSlider(currentSlide)
			resetProgressBar()
			document.querySelectorAll('.controls__button').forEach((button) => {
				button.classList.remove('controls__button--selected')
			})
			document
				.querySelector(`.controls__button[data-index="${slideIndex}"]`)
				.classList.add('controls__button--selected')
		}

		// & Para o slider
		const stopSlider = () => {
			clearInterval(intervalId)
		}

		// & Reseta a barra de progresso
		const resetProgressBar = () => {
			const progressBar = document.querySelector('.progress-bar')
			progressBar.style.transition = 'none'
			progressBar.style.width = '100%'
			setTimeout(() => {
				progressBar.style.transition = 'width 5s linear'
				progressBar.style.width = '100%'
			}, 50)
		}

		// & Alterna o valor de isPlaying , pausa a barra de progresso e alterna o ícone de play / pause
		// & Se isPlaying for verdadeiro, chama a função nextSlide e inicia o slider
		// & Se isPlaying for falso, chama a função stopSlider
		const pauseSlider = () => {
			isPlaying.value = !isPlaying.value
			const progressBar = progressBarRef.value
			progressBar.classList.toggle('paused')
			if (isPlaying.value) {
				startSlider(currentSlide.value)
			} else {
				stopSlider()
			}
		}

		// & Informa o slide atual para o elemento master do slider
		watch(currentSlide, () => {
			sliderRef.value.style.setProperty('--slide-index', currentSlide.value)
		})

		// & Para o slider quando o componente é desmontado
		onUnmounted(stopSlider)

		return {
			slides,
			currentSlide,
			changeSlide,
			sliderRef,
			progressBarRef,
			restartProgressBarAnimation,
			startSlider,
			stopSlider,
			isPlaying,
			pauseSlider,
			resetProgressBar
		}
	}
}
</script>
<style lang="sass" scoped>
.slider
	position: relative
	width: 300vw
	display: flex
	transition: .5s
	left: calc(var(--slide-index) * -100vw)
	z-index: -999

	&__darken
		position: absolute
		width: 100vw
		height: 100vh
		top: 0
		left: 0
		background-color: rgb(12, 8, 4)
		opacity: .5
		z-index: 1

	&__pattern
		position: absolute
		width: 100vw
		height: 100vh
		top: 0
		left: 0
		background: url(../../assets/images/pattern-7.png) repeat
		mix-blend-mode: multiply

	&__bottom
		width: 100vw
		height: 16px
		background-color: $light-gold
		position: absolute
		bottom: 0
		z-index: 9999

	&__box
		display: grid
		background-position: center
		grid-template-columns: 90px 270px auto
		grid-template-rows: auto 570px 180px
		grid-template-areas: "line1 line1 line1" "line2 line2 destaque" "line3 text text"
		position: relative
		width: 100vw
		height: 100vh

		&:nth-child(1)
			animation-delay: 0s

		&:nth-child(2)
			animation-delay: 7s

		&:nth-child(3)
			animation-delay: 14s

	&__video-wrapper
		position: absolute
		top: 0
		left: 0
		width: 100vw
		height: 100vh
		overflow: hidden
		z-index: -99

	&__video
		width: 100vw
		height: 100vh
		object-fit: cover

	&__content
		width: 100vw
		height: 100vh
		position: relative
		z-index: 9

	&__destaque
		grid-area: destaque
		font-family: 'npregular', sans-serif
		font-size: 5rem
		text-transform: uppercase
		color: $gold
		width: 100%
		height: 100%
		display: grid
		align-content: center
		width: 800px
		z-index: 9
		text-shadow: -2px 2px 4px rgba(0, 0, 0, 0.5)

	&__text
		grid-area: text
		color: $text-color
		font-size: 1.5rem
		width: 100%
		height: 100%
		display: grid
		align-content: center
		width: 600px
		z-index: 999

	&__line1
		grid-area: line1

	&__line2
		grid-area: line2

	&__line3
		grid-area: line3

.progress-bar
	background-color: $gold
	position: absolute
	width: 9px
	bottom: 0
	height: 0
	animation: fill 7s linear infinite
	animation-play-state: running

	&--bg
		background-color: $dark-gold
		position: absolute
		width: 9px
		bottom: 0
		height: 100vh
		opacity: .5

.controls
	width: 60px
	height: 320px
	grid-area: controls
	position: absolute
	left: 80px
	@include dflex(center, center, column)
	top: 0
	bottom: 0
	margin: auto

	&__button
		width: 12px
		height: 12px
		border-radius: 50%
		background-color: $gold
		position: relative
		border: none
		margin-bottom: 50px

		&::after
			content: ''
			position: absolute
			width: 36px
			height: 36px
			border-radius: 50%
			border: 2px solid $gold
			opacity: 0
			top: 50%
			left: 50%
			transform: translate(-50%, -50%)
			transition: opacity 0.3s ease

		&:last-child
			margin-bottom: 0

		&--selected
			&::after
				opacity: 1

		&--pause
			width: 100%
			height: auto
			background-color: transparent
			position: relative
			border: none

.paused
	animation-play-state: paused

.icon-pause, .icon-play
	font-size: 3rem
	margin-top: 40px
	color: $gold

@keyframes fill
	0%
		height: 0

	100%
		height: 100%

.scroll
	position: absolute
	right: 240px
	bottom: 40px
	width: 40px
	height: 70px
	border: 2px solid $light-gold
	border-radius: 25px
	display: flex
	place-content: center

.scroll:before
	position: absolute
	content: ''
	width: 10px
	height: 10px
	background: $light-gold
	border-radius: 5px
	top: 5px
	animation-duration: 2s
	animation-iteration-count: infinite
	animation-name: scroll

@keyframes scroll
	0%
		opacity: 1
	100%
		opacity: 0
		transform: translateY(46px)

.riscado
	text-decoration: line-through !important
	color: #ff6000
</style>

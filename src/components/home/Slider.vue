<template>
	<div class="slider" ref="sliderRef">
		<div
			class="slider__box"
			:key="index"
			:style="{
				backgroundImage: `url(${slide.backgroundImage})`
			}"
		>
			<div class="slider__destaque">
				{{ slide.title }}
			</div>
			<div class="slider__text">
				{{ slide.description }}
			</div>
		</div>
	</div>
	<div class="progress-bar--bg"></div>
	<div
		class="progress-bar"
		ref="progressBarRef"
		v-bind:style="{ height: progressBar + '%' }"
	></div>
	<div class="controls">
		<button class="controls__button" data-index="0" @click="changeSlide(0)"></button>
		<button class="controls__button" data-index="1" @click="changeSlide(1)"></button>
		<button class="controls__button" data-index="2" @click="changeSlide(2)"></button>
	</div>
</template>
<script>
import { ref, onMounted, onUnmounted, watch, computed } from 'vue'
export default {
	name: 'Slider',
	setup() {
		const slides = [
			{
				title: 'A 4ª Onda da Educação Digital Chegou aos Negócios ',
				description:
					'A melhor expêriencia de aprendizagem online chegou ao Brasil: Cohort-Based Learning',
				backgroundImage: '../../src/assets/images/bg-home.jpg'
			},
			{
				title: 'Você só aprende aquilo que pode aplicar de imediato na sua carreira',
				description:
					'Nossos cursos são desenvolvidos com base no mundo real, para que você possa aplicar o que aprendeu imediatamente',
				backgroundImage: '../../src/assets/images/bg-home-2.jpg'
			},
			{
				title: 'Vamos mudar a forma como o conhecimento de negócios é compartilhado',
				description:
					'Vamos levar a melhor experiência de aprendizado para os profissionais, por meio do melhor e mais inovador uso da tecnologia, e com uma combinação perfeita entre inspiração, conhecimento e prática.',
				backgroundImage: '../../src/assets/images/bg-home-4.jpg'
			}
		]

		const currentSlide = ref(0)
		const sliderRef = ref(null)
		const progressBarRef = ref(null)

		const progressBar = computed(() => {
			return (currentSlide.value / slideCount.value) * 100
		})

		const slideCount = computed(() => slides.length)

		const changeSlide = (index) => {
			stopSlider()
			currentSlide.value = index
			startSlider(currentSlide)
			restartProgressBarAnimation()
			document.querySelectorAll('.controls__button').forEach((button) => {
				button.classList.remove('controls__button--selected')
			})
			document
				.querySelector(`.controls__button[data-index="${index}"]`)
				.classList.add('controls__button--selected')
		}

		const restartProgressBarAnimation = () => {
			let progressBar = progressBarRef.value
			progressBar.style.animation = 'none'
			progressBar.offsetHeight // trigger reflow
			progressBar.style.animation = ''
		}

		let intervalId

		const startSlider = (currentSlide, restartProgressBarAnimation) => {
			intervalId = setInterval(() => {
				currentSlide.value = (currentSlide.value + 1) % slideCount.value
				setTimeout(restartProgressBarAnimation, 0)
				document.querySelectorAll('.controls__button').forEach((button) => {
					button.classList.remove('controls__button--selected')
				})
				document
					.querySelector(`.controls__button[data-index="${currentSlide.value}"]`)
					.classList.add('controls__button--selected')
			}, 7000)
		}

		const stopSlider = () => {
			clearInterval(intervalId)
		}

		watch(currentSlide, () => {
			sliderRef.value.style.setProperty('--slide-index', currentSlide.value)
		})

		onMounted(() => {
			startSlider(currentSlide)
			document
				.querySelector('.controls__button[data-index="0"]')
				.classList.add('controls__button--selected')
			restartProgressBarAnimation()
		})

		onUnmounted(stopSlider)

		return {
			slides,
			currentSlide,
			changeSlide,
			sliderRef,
			progressBarRef,
			restartProgressBarAnimation,
			progressBar
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

	&__text
		grid-area: text
		color: $text-color
		font-size: 1.5rem
		width: 100%
		height: 100%
		display: grid
		align-content: center
		width: 600px

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

	&--bg
		background-color: $dark-gold
		position: absolute
		width: 9px
		bottom: 0
		height: 100vh
		opacity: .5

.controls
	width: 60px
	height: 240px
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

@keyframes fill
	0%
		height: 0

	100%
		height: 100%
</style>

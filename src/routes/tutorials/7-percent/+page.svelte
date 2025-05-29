<script lang="ts">
	import { gsap } from 'gsap'
	import GSDevTools from 'gsap/dist/GSDevTools'

	gsap.registerPlugin(GSDevTools)

	let tl = $state(gsap.timeline())

	$effect(() => {
		GSDevTools.create()

		tl.set('emoji', {
			opacity: 0,
			y: 150,
			scale: 0.5,
		})

		tl.to('emoji', {
			keyframes: {
				'60%': {
					autoAlpha: 1,
					x: -75,
				},
				'100%': {
					x: 25,
					y: 350,
					scale: 1,
					rotate: -360 * 4,
				},
				ease: 'power1.in',
			},
			duration: 1,
			stagger: 0.75,
		}).fromTo(
			'h1',
			{
				x: -100,
				opacity: 0,
			},
			{
				x: 0,
				opacity: 1,
				ease: 'back',
			},
			'+=0.5',
		)
	})
</script>

<div class="relative h-[500px] w-full border text-center">
	<emoji>⚾</emoji>
	<emoji>⚾</emoji>
	<emoji>⚾</emoji>
</div>

<h1 class="text-center text-4xl font-bold">Strike 3, you're out!</h1>

<style>
	emoji {
		visibility: hidden;
	}
</style>

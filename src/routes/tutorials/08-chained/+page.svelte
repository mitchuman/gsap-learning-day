<script lang="ts">
	import { gsap } from 'gsap'
	import GSDevTools from 'gsap/dist/GSDevTools'

	gsap.registerPlugin(GSDevTools)

	let tl = $state(gsap.timeline())

	let basket = $state<any>()
	let ball = $state<any>()

	$effect(() => {
		GSDevTools.create()

		tl.from(basket, {
			x: 100,
		})
			.from(
				ball,
				{
					autoAlpha: 0,
					rotate: -360,
					x: -100,
					ease: 'power1.In',
				},
				'<',
			)
			.fromTo(
				ball,
				{ x: 0 },
				{
					x: 350 / 2,
					y: -200,
					filter: 'blur(3px)',
					rotate: 180,
				},
				'>',
			)
			.to(
				ball,
				{
					x: 350,
					y: -20,
					filter: 'blur(0px)',
					rotate: 360,
				},
				'>',
			)
	})
</script>

<div class="relative size-[400px] overflow-hidden border leading-none">
	<emoji bind:this={ball} class="absolute bottom-0 left-2">🏀</emoji>
	<emoji bind:this={basket} class="absolute right-2 bottom-0">🗑️</emoji>
</div>

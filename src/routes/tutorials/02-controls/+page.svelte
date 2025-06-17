<script lang="ts">
	import { gsap } from 'gsap'
	import Button from './Button.svelte'

	let race: gsap.core.Tween | null = $state(null)

	$effect(() => {
		race = gsap.to('#car', {
			x: '95vw',
			ease: 'sine.inOut',
			duration: 3,
			paused: true,
		})

		gsap.fromTo(
			'#flag',
			{
				rotate: 0,
			},
			{
				rotate: 360,
				repeat: -1,
				transformOrigin: 'bottom left',
				duration: 1,
			},
		)
	})
</script>

<div class="flex justify-between">
	<emoji id="car" class="z-1 -scale-x-100">🏎️</emoji>
	<emoji id="flag">🏁</emoji>
</div>

<Button onclick={() => race?.play()}>GO!</Button>
<Button onclick={() => race?.pause()}>STOP! 🛑</Button>
<Button onclick={() => race?.reverse()}>REVERSE! ⏪</Button>
<Button onclick={() => race?.restart()}>RESTART! 🔁</Button>

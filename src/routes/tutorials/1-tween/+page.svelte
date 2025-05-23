<script lang="ts">
	import { gsap } from 'gsap'

	gsap.defaults({
		duration: 5,
	})

	$effect(() => {
		gsap.fromTo(
			'.sho',
			{
				x: '-100%',
			},
			{
				x: '100%',
				rotateY: 360,
				repeat: -1,
				yoyo: true,
			},
		)

		gsap.from('emoji', {
			y: -400,
			duration: 1,
			ease: 'bounce.out',
			rotate: -180,
			stagger: {
				amount: 2,
			},
			delay: 1.5,
		})
	})
</script>

<div class="grid items-end gap-4 *:col-span-full *:row-span-full">
	<div class="flex gap-4">
		<emoji>⚾</emoji>
		<emoji>⚾</emoji>
		<emoji>⚾</emoji>
		<emoji>⚾</emoji>
		<emoji>⚾</emoji>
	</div>
	<img class="sho" src="/sho.png" alt="" />
</div>

<script lang="ts">
	import { gsap } from 'gsap'
	import GSDevTools from 'gsap/dist/GSDevTools'
	import { TextPlugin } from 'gsap/dist/TextPlugin'
	import { SplitText } from 'gsap/dist/SplitText'

	gsap.registerPlugin(GSDevTools, TextPlugin, SplitText)

	let tl: gsap.core.Timeline = $state(gsap.timeline())
	let bart: gsap.core.Timeline = $state(gsap.timeline())

	const BART_TORTURE = 10

	$effect(() => {
		// GSDevTools.create()

		gsap.to('#abc123', {
			text: 'ABCDEFGHI',
			duration: 1,
			ease: 'none',
			repeat: -1,
			yoyo: true,
		})

		gsap.set('#splittext', { autoAlpha: 1 })

		let chars = new SplitText('#splittext', { type: 'chars' })
		tl.from(chars.chars, { opacity: 0, yPercent: 20, ease: 'back(10)', rotate: -6, stagger: 0.05 })

		let lines = new SplitText('#paragraph', { type: 'lines' })
		tl.from(
			lines.lines,
			{ opacity: 0, rotationX: -90, rotateY: 45, transformOrigin: '50% 50% -100', stagger: 0.05 },
			'-=0.25',
		)

		bart
			.to('#chalkboard p', {
				text: 'I will not fake my way through life.',
				duration: 1,
				stagger: 1,
				ease: 'none',
			})
			.to(
				'#chalkboard img',
				{
					x: '28ch',
					duration: 1,
					repeat: BART_TORTURE - 1,
					ease: 'none',
				},
				'<',
			)
	})
</script>

<section id="typewriter" class="p-4">
	<h1 id="abc123" class="font-mono text-3xl font-bold">123456789</h1>
	<h1 id="splittext" class="invisible text-3xl font-bold text-[dodgerblue]">Shohei Ohtani</h1>

	<p id="paragraph" class="max-w-sm perspective-distant">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati, officia omnis veritatis
		perferendis esse minus eius alias ipsum magni facilis recusandae sapiente expedita ad molestiae?
		Doloremque fugit possimus id libero minus iusto delectus dignissimos neque adipisci, quisquam ad
		earum nobis cupiditate illum quibusdam veniam cum impedit eos. Odio, illo id?
	</p>
</section>

<section
	id="chalkboard"
	class="relative mt-12 h-[calc(3lh+var(--lines)*1lh)] border-b-12 border-[#8b4513] bg-[darkgreen] p-4 font-[cursive] text-white"
	style:--lines={BART_TORTURE}
>
	{#each Array(BART_TORTURE) as _, i}
		<p></p>
	{/each}

	<!-- image of bart simpson -->
	<img class="h-[6lh] -translate-y-1/2" src="/bart.png" alt="" />
</section>

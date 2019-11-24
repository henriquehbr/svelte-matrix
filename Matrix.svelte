<script>
	import { onMount } from 'svelte'

	export let chars = 'ﾊﾐﾋｰｳｼﾅﾓﾆｻﾜﾂｵﾘｱﾎﾃﾏｹﾒｴｶｷﾑﾕﾗｾﾈｽﾀﾇﾍ'.split('')
	export let width
	export let height
	export const noInitialDrop = false
	export const fontSize = 16
	export const color = '#0f0'
	export const interval = 33

	let canvas
	let windowWidth = 300
	let windowHeight = 150

	$: cols = Math.round((width ? width : windowWidth) / fontSize)
	$: drops = Array(cols).fill(noInitialDrop ? (height ? height : windowHeight) : 0)

	const sleep = ms => new Promise(resolve => setTimeout(resolve, ms))

	onMount(async () => {
		// Sync canvas dimensions with window
		[windowWidth, windowHeight] = await [window.innerWidth, window.innerHeight]
		const ctx = canvas.getContext('2d')
		while (true) {
			// Black bg for the canvas, translucent to show trail
			ctx.fillStyle = 'rgba(0, 0, 0, 0.05)'
			ctx.fillRect(0, 0, canvas.width, canvas.height)
			
			// Green text
			ctx.fillStyle = color
			ctx.font = `${fontSize}px arial`

			// Looping
			for (let i = 0; i < drops.length; i++) {
				// Displays a random character from chars
				const randomChar = Math.floor(Math.random() * chars.length)
				const text = chars[randomChar]
				ctx.fillText(text, i * fontSize, drops[i] * fontSize)
				const reachedEndOfScreen = drops[i] * fontSize > canvas.height && Math.random() > 0.975
				if (reachedEndOfScreen) drops[i] = 0
				drops[i]++
			}
			await sleep(interval)
		}
	})
</script>

<svelte:window bind:innerWidth={windowWidth} bind:innerHeight={windowHeight} />

<canvas bind:this={canvas} width={width ? width : windowWidth} height={height ? height : windowHeight}></canvas>

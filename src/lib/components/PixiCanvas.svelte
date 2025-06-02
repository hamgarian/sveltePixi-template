<script lang="ts">
	import { onMount } from 'svelte';
	import { Application, Assets, Sprite } from 'pixi.js';

	let pixiContainer: HTMLDivElement;

	onMount(async () => {
		// Create a new application
		const app = new Application();

		// Initialize the application
		await app.init({ background: '#f1bcce', resizeTo: window });

		// Append the application canvas to the container
		pixiContainer.appendChild(app.canvas);

		// Load the texture
		const texture = await Assets.load('/assets/bunny.png');

		// Create a Sprite
		const bunny = new Sprite(texture);

		// Set anchor to center
		bunny.anchor.set(0.5);

		// Scale the sprite
		bunny.scale.set(1);

		// Position the sprite in the center of the screen
		bunny.position.set(app.screen.width / 2, app.screen.height / 2);

		// Add sprite to the stage
		app.stage.addChild(bunny);

		// Rotate the sprite continuously
		app.ticker.add((time) => {
			bunny.rotation += 0.1 * time.deltaTime;
		});
	});
</script>

<div bind:this={pixiContainer} class="w-full h-full"></div>

<style>
	div {
		width: 100%;
		height: 100vh;
		overflow: hidden;
	}
</style>

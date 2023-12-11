<script>
	import Header from './Header.svelte';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';

	let showCookie = false;

	onMount(async () => {
		let p1 = new Promise((res) => setTimeout(res, 5000));
		p1.then(() => (showCookie = true));
	});
</script>

<div class="row dark">
	<div class="sm-6 md-8 lg-1 col" />
	<div class="sm-6 md-8 lg-10 col">
		<Header />

		<main>
			<slot />
		</main>

		<footer>
			<p>Built to learn <a href="https://kit.svelte.dev">SvelteKit</a></p>
		</footer>
		{#if showCookie}
			<div class="footer">
				<input class="alert-state" id="alert-2" type="checkbox" />
				<div
					class="alert alert-secondary dismissible border"
					transition:fly={{ y: 200, duration: 2000 }}
				>
					<p>
						This page does not store any cookies. Partly because, I am vegan and I am not sure what
						to do with your cookies.
					</p>
					<label class="btn-close" for="alert-2">Yeah Fine</label>
				</div>
			</div>
		{/if}
	</div>
	<div class="sm-6 md-4 lg-1 col" />
</div>

<style>
	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
	.footer {
		position: fixed;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 90px;
		/*background-color: #D0DAEE;*/
	}
</style>

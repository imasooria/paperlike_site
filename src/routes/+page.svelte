<script>
	import { onMount } from 'svelte';
	import About from './About.svelte';
	import { fly } from 'svelte/transition';

	let getInfo = false;
	let preFerNotToSay = false;

	onMount(async () => (getInfo = true));

	let humanSpecies = true;
	let userSpecies = '';

	let getUser = (humanSpecies, userSpecies) => {
		if (preFerNotToSay) {
			return 'who ever you are';
		} else if (humanSpecies) {
			return 'Fellow Human';
		} else if (userSpecies.length < 1) {
			return '🧐';
		} else {
			return userSpecies;
		}
	};
	$: greetUser = getUser(humanSpecies, userSpecies, preFerNotToSay);

	let planetEarth = true;
	let userPlanet = '';
</script>

<div class="container-lg paper border">
	<h2>Hello {greetUser}</h2>
	<About />

	<input class="modal-state" id="onload-modal" type="checkbox" bind:checked={getInfo} />
	<div class="modal border">
		<label class="modal-bg" for="onload-modal" />
		<div class="modal-body">
			<h4 class="modal-title">Some basic info first</h4>
			<h5 class="modal-subtitle">Who are you ?</h5>
			<fieldset class="form-group">
				<label for="paperChecks2" class="paper-check">
					<input type="checkbox" name="paperChecks" id="paperChecks2" bind:checked={humanSpecies} />
					<span>Human</span>
				</label>
				{#if !humanSpecies}
					<input bind:value={userSpecies} type="text" placeholder="Enter your Species" />
				{/if}
			</fieldset>

			<h5 class="modal-subtitle">Where are you from ?</h5>
			<fieldset class="form-group">
				<label for="paperChecks1" class="paper-check">
					<input type="checkbox" name="paperChecks" id="paperChecks1" bind:checked={planetEarth} />
					<span>Earth</span>
				</label>
				{#if !planetEarth}
					<input bind:value={userPlanet} type="text" placeholder="Enter your planet" />
				{/if}
			</fieldset>

			<button
				class="btn-small btn-danger"
				on:click={() => {
					getInfo = false;
					preFerNotToSay = true;
				}}>prefer not to Say</button
			>
			{#if greetUser.length > 0 && (planetEarth || userPlanet.length > 0)}
				<button class="btn-small btn-secondary" on:click={() => (getInfo = false)}>Done</button>
			{/if}
		</div>
	</div>
</div>

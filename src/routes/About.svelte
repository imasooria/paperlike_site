<script>
	import surya from '$lib/images/surya.png';
	import { fade, fly } from 'svelte/transition';
	import { flip } from 'svelte/animate';

	let languages = [
		'Lua',
		'Scala',
		'Haskell',
		'Go',
		'C',
		'C++',
		'Perl',
		'Java',
		'Bash',
		'Python',
		'Javascript'
	];
	let prof = 40;
	$: proficiency = calculateProficiency(prof) || 'slide to know';
	const calculateProficiency = (prof) => {
		if (prof < 10) {
			return 'Can Write Hello World';
		} else if (prof >= 10 && prof <= 40) {
			return 'Can build Application using Stack overflow';
		} else if (prof > 40 && prof < 80) {
			return 'Can build Applications with out Stack overflow';
		} else if (prof > 80) {
			return 'Can rewrite the Compiler';
		}
	};
	$: p2 = getProf(prof);
	const getProf = (prof) => {
		if (prof < 10) {
			return [0, 10];
		} else if (prof >= 10 && prof <= 40) {
			return [3, 11];
		} else if (prof > 40 && prof <= 80) {
			return [8, 11];
		} else if (prof > 80) {
			return [11, 12];
		}
	};
</script>

<div class="container-lg paper border">
	<h3>
		<img src={surya} alt="surya" class="float-right responsive" width="600" height="400" />

		☀️ I am SuryaTeja Iriventi. Call me
		<p style="display:inline" popover-top="/suurjə/">Surya</p>
		<br />
		👨‍💻 Software developer by profession. <br />
		🏙️ Living in Hyderabad.<br />
		👍 Likes : Programming 💻, Badminton 🏸<br />
		🫶🏽 Hobbies: Film Making 🎬
		<a href="https://www.youtube.com/c/markatarashi" target="_blank"> (check out) </a>, Computer
		Games 🎮🕹️👾 <br />
		👎 Dislikes: Nothing in particular 🧘‍♂️<br />
	</h3>
</div>

<div class="container-lg paper border">
	<h3>
		Programming languages - by proficiency !
		<fieldset class="form-group">
			<div class="form-group">
				<input class="input-block" type="range" min="0" max="100" bind:value={prof} />
				<p>
					<output id="output" for="percentage"><span class="badge ">{proficiency}</span></output>
				</p>
			</div>
		</fieldset>
		<div class="cntr">
			{#each languages.slice(p2[0], p2[1]) as item, i}
				<div in:fly={{ y: 200, duration: 2000 }} out:fly={{ x: 200, duration: 2000 }}>
					<p><span class="badge secondary">{item}</span></p>
				</div>
			{/each}
		</div>
	</h3>
</div>

<style>
	.responsive {
		width: 20%;
		height: auto;
	}
	.cntr {
		display: flex; /* or inline-flex */
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: space-evenly;
	}

</style>

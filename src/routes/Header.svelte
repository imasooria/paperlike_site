<script>
	let darkTheme = false;
	$: theme = darkTheme ? 'dark' : 'light';
</script>

<nav class="border fixed split-nav">
	<div class="nav-brand">
		<h3><a href="#">Masooria</a></h3>
	</div>
	<div class="collapsible">
		<div class="collapsible-body">
			<ul class="inline">
				<li><a href="#">About</a></li>
				<li><a href="#">Blog</a></li>
				<li><a href="#">Contact</a></li>
			</ul>
		</div>
	</div>
	<fieldset class="form-group">
		<label for="themeSwitch" class="paper-switch-2-label">
			Theme - {theme}
		</label>
		<label class="paper-switch-2">
			<input id="themeSwitch" name="themeSwitch" type="checkbox" bind:checked={darkTheme} />
			<span class="paper-switch-slider round" />
		</label>
	</fieldset>
</nav>
<input class="modal-state" type="checkbox" bind:checked={darkTheme} />
<div class="modal border">
	<label class="modal-bg" />
	<div class="modal-body">
		<h4 class="modal-title">Still learning how to implement dark theme</h4>
		<h5 class="modal-subtitle">Toggle back theme to light</h5>
	</div>
</div>

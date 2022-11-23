<script>

</script>

<div class="viewport">
  <div class="screen">
    <slot></slot>
  </div>
</div>

<style>
  	.viewport {
		width: 80%;
		height: 4em;
		overflow: hidden;
		text-align: center;
		position: relative;
    margin: 0 1em;
    background-color: var(--LC-background);
		border-right: .2em solid var(--darken-color);
		border-top: .2em solid var(--darken-color);
		border-left: .2em solid var(--secondary-color);
		border-bottom: .2em solid var(--secondary-color);
    box-shadow: -.2em .2em .1em rgba(0, 0, 0, 0.3) inset;
	}

	.screen {
    font-family: var(--font-mono);
    -webkit-filter: drop-shadow(-.1em .1em .1em #0f2a3260);
    filter: drop-shadow(-.1em .1em .1em #0f2a3260);
    text-shadow: -.1em .1em .1em #0f2a3260;
		color: var(--LC-content);
		position: absolute;
		width: 100%;
		height: 100%;
	}
</style>
<script>
	import { spring } from 'svelte/motion';

	let count = 0;

	const displayed_count = spring();
	$: displayed_count.set(count);
	$: offset = modulo($displayed_count, 1);

	/**
	 * @param {number} n
	 * @param {number} m
	 */
	function modulo(n, m) {
		// handle negative numbers
		return ((n % m) + m) % m;
	}
</script>

<div class="counter">
  <div class="button-wrap">
    <button on:click={() => (count -= 1)} aria-label="Decrease the counter by one">
      <span>-</span>
    </button>
  </div>

	<div class="counter-viewport">
		<div class="counter-digits" style="transform: translate(0, {100 * offset}%)">
			<strong class="hidden" aria-hidden="true">{Math.floor($displayed_count + 1)}</strong>
			<strong>{Math.floor($displayed_count)}</strong>
		</div>
	</div>

  <div class="button-wrap">
    <button on:click={() => (count += 1)} aria-label="Increase the counter by one">
      <span>+</span>
    </button>
  </div>
</div>

<style>
	.counter {
		display: flex;
		margin: 1rem 0;
	}

  .counter .button-wrap{
		width: 2em;
		padding: .1em;
    background-color: var(--black-color);
    border-radius: .3em;
    box-shadow: -.1em .1em .2em rgba(0,0,0,0.2);
		font-size: 2rem;
  }

	.counter button {
		width: 100%;
    height: 100%;
		padding: 0;
		border-left: .1em solid var(--darken-color);
		border-bottom: .1em solid var(--darken-color);
		border-right: .1em solid var(--secondary-color);
		border-top: .1em solid var(--secondary-color);
    border-radius: .2em;
		touch-action: manipulation;
		background-color: var(--tertiary-color);
    box-shadow: .2em -.2em .3em rgba(255, 255, 255, 0.3) inset;
		color: var(--text-color);
    font-weight: 700;
		font-size: 36px;
	}

	.counter .button-wrap:active {
    box-shadow: -.02em .02em .2em rgba(0,0,0,0.2);
	}

  .counter button span{
    position: relative;
    top: -.05em;
  }

	svg {
		width: 25%;
		height: 25%;
	}

	path {
		vector-effect: non-scaling-stroke;
		stroke-width: 2px;
		stroke: var(--text-color);
	}

	.counter-viewport {
		width: 6em;
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

	.counter-viewport strong {
		position: absolute;
		display: flex;
		width: 100%;
		height: 100%;
		font-weight: 400;
		color: var(--LC-content);
		font-size: 72px;
		align-items: center;
		justify-content: center;
	}

	.counter-digits {
    font-family: var(--font-mono);
    text-shadow: -.1em .1em .1em #0f2a3260;
		position: absolute;
		width: 100%;
		height: 100%;
	}

	.hidden {
		top: -100%;
		user-select: none;
	}
</style>

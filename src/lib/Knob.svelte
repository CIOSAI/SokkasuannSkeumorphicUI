<script lang="js">
	export let value = 0, min = 0, max = 1;
	export let rotRange = 2 * Math.PI * 0.83;
	export let pixelRange = 200;
	export let startRotation = -Math.PI * 0.83;
	
	let startX = 0, startValue = 0;
	$: valueRange = max - min;
	$: rotation = startRotation + (value - min) / valueRange * rotRange;
	
	function clamp(num, min, max) {
		return Math.max(min, Math.min(num, max));
	}
	
	function pointerMove({ clientX }) {
		const valueDiff = valueRange * (startX - clientX) / pixelRange;
		value = clamp(startValue - valueDiff, min, max)
	}
	
	function pointerDown({ clientX }) {
		console.log({ clientX });
		startX = clientX;
		startValue = value;
		window.addEventListener('pointermove', pointerMove);
		window.addEventListener('pointerup', pointerUp);
	}
	
	function pointerUp() {
		window.removeEventListener('pointermove', pointerMove);
		window.removeEventListener('pointerup', pointerUp);
	}
</script>

<div class='knob-container'>
  <div class="knob" style="transform:rotate(calc({rotation} * 1rad))" on:pointerdown={pointerDown} >
    <svg width='100%' height='100%' viewBox="0 0 100 100">
      <g fill="none" stroke="currentColor">
        <path stroke-width="10" d="M50 40 l0 -50" />
      </g>
    </svg>
  </div>
</div>

<style>
  .knob-container{
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    width: 40px;
    height: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-image: conic-gradient(from 45deg,
      var(--secondary-color) 0deg 15deg,
      var(--tertiary-color) 60deg 60deg,
      var(--darken-color) 120deg 240deg,
      var(--tertiary-color) 300deg 300deg,
      var(--secondary-color) 345deg 360deg
    );
    box-shadow: -.15em .15em .05em .02em rgba(0,0,0,0.3);
    border-radius: 50%;
  }  

  .knob {
    display: block;
    width: 80%;
    height: 80%;
    padding: 0;
    border-radius: 50%;
    color: var(--text-color);
    background-color: var(--tertiary-color);
    box-shadow: 0 0 .3em rgba(255, 255, 255, 0.3) inset;
    transform-origin: 50% 50%;
  }

  .knob svg{
    width: 100%;
    height: 100%;
  }
</style>


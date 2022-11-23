<script>
	import Counter from '$lib/Counter.svelte';
  import Slider from '$lib/Slider.svelte';
  import Knob from '$lib/Knob.svelte';
  import Screen from '$lib/Screen.svelte';

  let knob_values = {a: 0, d: 0, s: 0, r: 0};
  $: console.log(knob_values)
</script>

<svelte:head>
	<title>Sokkasuann</title>
	<meta name="description" content="Skeumorphic UI" />

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Atkinson+Hyperlegible:ital,wght@0,400;0,700;1,400;1,700&family=JetBrains+Mono:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800&display=swap" rel="stylesheet">
</svelte:head>

<section>

  <div class='counter-panel'>
    <span class='title'>Echo Ticker 2000</span>
    <div style='height: 10px'/>
    <Counter />
    <div style='height: 20px'/>
    <div class='slider-container'>
      <span class='label'>Chadness</span>
      <Slider />
    </div>
    <div style='height: 20px;'/>
    <div class='knob-container'>
      <span class='label'>Envelope</span>
      <div class='knob-array'>
        <div class='knob-col'>
          <span class='label' style='user-select: none'>A</span>
          <Knob bind:value={knob_values.a} max={1} min={0} pixelRange={50} />
        </div>
        <div class='knob-col'>
          <span class='label' style='user-select: none'>D</span>
          <Knob bind:value={knob_values.d} max={1} min={0} pixelRange={50} />
        </div>
        <div class='knob-col'>
          <span class='label' style='user-select: none'>S</span>
          <Knob bind:value={knob_values.s} max={1} min={0} pixelRange={50} />
        </div>
        <div class='knob-col'>
          <span class='label' style='user-select: none'>R</span>
          <Knob bind:value={knob_values.r} max={1} min={0} pixelRange={50} />
        </div>
      </div>
    </div>
    <div style='height: 20px;'/>
    <div class='screen-container'>
      <Screen>
        <svg width='100%' height='100%' viewBox="0 0 300 100">
          <g fill="none" stroke="currentColor" stroke-width='10' stroke-linejoin="bevel">
            <path d="M0 80 L5 80 
              L{knob_values.a*100+5} 20 
              l{knob_values.d*150} {60-knob_values.s*60} 
              l{knob_values.r*100} {knob_values.s*60} L300 80
            "/>
          </g>
        </svg>
      </Screen>
    </div>
  </div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

  .title{
    width: 100%;
    font-size: 36px;
    font-style: italic;
    font-weight: 700;
    color: var(--text-color);
  }

  .slider-container{
    padding: .2em .7em;
    border: 3px solid var(--text-color);
    border-radius: 0 .4em .4em .4em;
  }

  .knob-container{
    padding: .2em .7em;
    border: 3px solid var(--text-color);
    border-radius: 0 .4em .4em .4em;
  }

  .knob-array{
    display: flex;
    justify-content: space-evenly;
  }

  .knob-col{
    text-align: center;
  }

  .label{
    width: 100%;
    font-size: 20px;
    font-weight: 700;
    color: var(--text-color);
  }

  .counter-panel{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: stretch;
    padding: 1em;
		border-left: .4em solid var(--darken-color);
		border-bottom: .4em solid var(--darken-color);
		border-right: .4em solid var(--secondary-color);
		border-top: .4em solid var(--secondary-color);
    border-radius: .2em;
		background-color: var(--tertiary-color);
    box-shadow: -.1em .1em .2em rgba(0,0,0,0.2);
    font-size: 24px;
  }
</style>

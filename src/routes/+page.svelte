<script>
	import Counter from '$lib/Counter.svelte';
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
    <Counter />
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

  .counter-panel{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
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

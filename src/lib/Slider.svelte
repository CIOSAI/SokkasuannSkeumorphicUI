<script lang="ts">
  export let value = 0;
</script>

<div id='container'>
  <input type='range' min='0' max='1' step='0.00000001'
    bind:value
  >
</div>

<style>
  #container{
    height: 3em;
    display: flex;
    align-items: center;
  }

  input{
    width: 100%;
    -webkit-appearance: none;  /* Override default CSS styles */
    appearance: none;
    height: .3em;
    background-color: var(--black-color);
  }
  
  input::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
		border-left: .1em solid var(--darken-color);
		border-bottom: .2em solid var(--darken-color);
		border-right: .1em solid var(--secondary-color);
		border-top: .2em solid var(--secondary-color);
    width: .7em;
    height: 2em;
    border-radius: 10%;
    background-color: var(--tertiary-color);
  }

  input::-moz-range-thumb {
		border-left: .1em solid var(--darken-color);
		border-bottom: .2em solid var(--darken-color);
		border-right: .1em solid var(--secondary-color);
		border-top: .2em solid var(--secondary-color);
    box-shadow: -.25em .15em .05em .05em rgba(0,0,0,0.3);
    width: .7em;
    height: 2em;
    border-radius: 10%;
    background: var(--tertiary-color);
  }

</style>
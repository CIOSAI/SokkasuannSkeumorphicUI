<script lang="ts">
  let slider_x = 0;
  $: console.log(slider_x);
</script>

<div id='container'>
  <input type='range' min='0' max='1' step='0.00000001'
    bind:value={slider_x}
  >
  <span id='knob-head-container'>
    <span id='knob-head'>
      <span id='notch'
        style:--rotation="{slider_x}"
      >
        <div style={`
          position: absolute; display: block; 
          left: 50%;
          top:50%; width: 4px; height: 50%; 
          background-color: var(--text-color);
        `}/>
      </span>
    </span>
  </span>
</div>

<style>
  #container{
    align-items: center;
    position: relative;
    width: 50px;
    height: 0;
    padding-bottom: 50px;
    margin-bottom: 5px;
  }

  input{
    -webkit-appearance: none;  /* Override default CSS styles */
    appearance: none;
    width: 100%;
    height: 50px;
    opacity: 0;
  }

  #knob-head-container{
    pointer-events: none;
    width: 100%;
    height: 100%;
    z-index: 10;
    top: 0;
    left: 0;
    position: absolute;

    border-radius: 50%;
    border: 3px solid var(--black-color);
  }

  #knob-head{    
    -webkit-box-sizing: border-box; /* Safari/Chrome, other WebKit */
    -moz-box-sizing: border-box;    /* Firefox, other Gecko */
    box-sizing: border-box;         /* Opera/IE 8+ */
    
    display: block;
    height: 100%;
    
    border-radius: 50%;
		border-left: .2em solid var(--darken-color);
		border-bottom: .2em solid var(--darken-color);
		border-right: .2em solid var(--secondary-color);
		border-top: .2em solid var(--secondary-color);
    background-color: var(--tertiary-color);
  }

  #notch{
    display: block;
    height: 100%;
    transform: rotate(var(--rotation)turn);
  }
  
  input::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    opacity: 0;
  }

  input::-moz-range-thumb {
    -webkit-appearance: none;
    appearance: none;
    opacity: 0;
  }

</style>
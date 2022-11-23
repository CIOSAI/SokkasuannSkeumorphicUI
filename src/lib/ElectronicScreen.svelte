<script lang="ts">
  export let textContent = '';
</script>

<div class="viewport">
  <textarea class="screen" spellcheck="false" disabled={true}>{textContent}</textarea>
</div>

<style>
  .viewport{
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    height: 100%;
    background-color: #222;
		border-right: .5em solid var(--darken-color);
		border-top: .5em solid var(--darken-color);
		border-left: .5em solid var(--secondary-color);
		border-bottom: .5em solid var(--secondary-color);
    padding: 1em;
  }
  .screen{
    height: 100%;
    width: 100%;
    top: 0;
    background: none;
    border: none;
    outline: none;
    padding: none;
    margin: none;
    font-size: inherit;
    color: var(--pure-white);
    font-family: var(--font-mono);
    text-shadow: 0 0 2em #ffffff80;
    /* word-wrap: break-word;
    overflow-wrap: break-word; */
    resize: none;
    overflow: hidden;
  }
  .screen::-webkit-scrollbar {
    display: none;
  }
</style>
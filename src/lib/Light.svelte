<script lang="ts">
  export let status = false;
</script>

{#if status}
  <div class='light-on'/>
{:else}
  <div class='light-off'/>
{/if}

<style>
  .light-on{
    width: .5em;
    height: .5em;
    background-color: rgb(255, 230, 238);
    border-radius: 50%;
    box-shadow: 0 0 .6em .3em rgba(255, 0, 81, 0.332);
  }

  .light-off{
    width: .5em;
    height: .5em;
    background-color: rgb(127, 32, 62);
    border-radius: 50%;
    box-shadow: -.1em .1em .2em rgba(0,0,0,0.2);
  }
</style>
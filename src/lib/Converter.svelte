<script lang="ts">
  let inputrate: number = 0;
  let outputrate: number = 0;

  const convert = () => {
    outputrate = (inputrate * 60 * 60 * 24) / 1024 / 1024;
    // now round this number
    outputrate = Math.round(outputrate * 100) / 100;
  };
</script>

<div class="converter">
  <div>
    <input type="text" bind:value={inputrate} /> MB/sec
  </div>

  <div>
    <button on:click={convert}> Convert </button>
  </div>
  <div>
    <strong>{outputrate} TB/day</strong>
  </div>
</div>

<style>
  .converter {
    display: flex;
    align-items: center;
    gap: 2em;
  }
</style>

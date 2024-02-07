<script lang="ts">
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
  import Converter from './lib/Converter.svelte';
</script>

<main>
  <h1>Rate converter</h1>
  <p>Rate a minute</p>

  <div class="card">
    <Converter />
  </div>

</main>

<style>
</style>

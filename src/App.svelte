<script lang="ts">
  import Converter from './lib/Converter.svelte';
</script>

<header>
  <h1>Rate converter</h1>
  <p>Hold up, rate a minute</p>
</header>
<main>
  <div class="card">
    <Converter />
  </div>
</main>

<style>
  header {
    display: flex;
    align-items: center;
    gap: 1em;
  }
</style>

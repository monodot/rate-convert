<script lang="ts">
  let rate: number = 0; // source rate
  let rateInTB: number; // rate in TB/day
  let unit = 'MB/sec'; // source unit

  // Conversion factors
  const MB_TO_TB = 1 / (1024 * 1024); // Conversion factor from MB to TB
  const GB_TO_TB = 1 / 1024; // Conversion factor from GB to TB
  const SEC_TO_DAY = 24 * 60 * 60; // Conversion factor from sec to day
  const MIN_TO_DAY = 24 * 60; // Conversion factor from min to day
  const HOUR_TO_DAY = 24; // Conversion factor from hour to day

  // Whenever rate or unit changes, recalculate rateInTB
  $: {
    let rateInTBPerDay;
    switch (unit) {
      case 'MB/sec':
        rateInTBPerDay = (rate * MB_TO_TB) * SEC_TO_DAY;
        break;
      case 'MB/min':
        rateInTBPerDay = (rate * MB_TO_TB) * MIN_TO_DAY;
        break;
      case 'GB/hour':
        rateInTBPerDay = (rate * GB_TO_TB) * HOUR_TO_DAY;
        break;
    }
    rateInTB = rateInTBPerDay || 0;
    rateInTB = Math.round(rateInTB * 100) / 100;

    // outputrate = Math.round(outputrate * 100) / 100;

  }
</script>

<div class="converter">
  <div class="card input">
    <div>Input</div>
    <div>
      <label>
        Rate:
        <input type="number" id="src_val" bind:value={rate}>
      </label>
      <label>
        Unit:
        <select bind:value={unit}>
          <option>MB/sec</option>
          <option>MB/min</option>
          <option>GB/hour</option>
        </select>
      </label>
    </div>
  </div>

  <div class="card output">
    <div>
      <span id="dst_val">{rateInTB}</span>
      <span id="dst_unit">TB/day</span>
    </div>
  </div>
</div>

<style>
  .converter {
    display: flex;
    align-items: center;
    gap: 2em;
  }

  .card {
    padding: 1.5rem;
    border-radius: 0.5rem;
    height: 6rem;
  }

  .converter .input {
    background: #FDCBD6;
  }
  .converter .output {
    background: #D3E3CE;
  }

  #src_val {
    width: 12ch;
  }
  #dst_val {
    font-size: 2.5rem;
    font-weight: bold;
  }
</style>

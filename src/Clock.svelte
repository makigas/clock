<script>
  import TimeZone from "./TimeZone.svelte";

  const UBICACIONES = [
    ["Madrid", "Europe/Madrid"],
    ["Canarias", "Atlantic/Canary"],
    ["UTC", "Etc/UTC"],
    ["Berlín", "Europe/Berlin"],
    ["Ciudad de México", "America/Mexico_City"],
    ["Bogotá", "America/Bogota"],
    ["Quito / Guayaquil", "America/Guayaquil"],
    ["Lima", "America/Lima"],
    ["Santiago de Chile", "America/Santiago"],
    ["Sucre / La Paz", "America/La_Paz"],
    ["Santo Domingo", "America/Santo_Domingo"],
    ["Buenos Aires", "America/Buenos_Aires"],
  ];

  let current = 0;

  const jump = () => {
    if (++current == UBICACIONES.length / 2) current = 0;
  };

  let interval;

  $: {
    if (interval) clearInterval(interval);
    interval = setInterval(() => {
      jump();
    }, 15000);
  }
</script>

<svg class="clock" viewBox="0 0 240 80">
  <TimeZone
    label={UBICACIONES[2 * current][0]}
    zone={UBICACIONES[2 * current][1]}
  />
</svg>

<svg class="clock" viewBox="0 0 240 80">
  <TimeZone
    label={UBICACIONES[2 * current + 1][0]}
    zone={UBICACIONES[2 * current + 1][1]}
  />
</svg>

<style>
  body {
    margin: 0;
    padding: 0;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: row;
  }
  .clock {
    margin: 0;
    padding: 0;
    margin-bottom: 10vh;
    width: 100vw;
    flex: 1;
  }
</style>

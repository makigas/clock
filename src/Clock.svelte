<script>
	import TimeZone from './TimeZone.svelte';
	
	const UBICACIONES = [
		["Madrid", "Europe/Madrid"],
		["Canarias", "Atlantic/Canary"],
		["UTC", "Etc/UTC"],
		["Ciudad de México", "America/Mexico_City"],
		["Santiago de Chile", "America/Santiago"],
		["La Paz", "America/La_Paz"],
		["Buenos Aires", "America/Buenos_Aires"],
		["Pyongyang", "Asia/Pyongyang"],
	]

	let current = 0;

	const jump = () => {
		if (++current == UBICACIONES.length)
			current = 0;
	}

	let interval;
	
	$: {
		if (interval)
			clearInterval(interval);
		interval = setInterval(() => {
			jump();
		}, 15000);
	}
</script>

<svg id="clock" viewBox="0 0 240 80">
	<TimeZone label={UBICACIONES[current][0]} zone={UBICACIONES[current][1]} />
</svg>

<style>
	#clock {
		position: absolute;
		width: 100vw;
		height: 100vh;
	}
</style>


<script>
	export let label;
	export let zone;
	export let className;

	let interval = null;
	let clock = null;

	const getTime = () => {
		let date = new Date();
		return date.toLocaleTimeString("es-ES", { timeZone: zone });
	}

	const updateTime = () => {
		clock = getTime();
	}
	
	$: {
		updateTime();
		if (interval) clearInterval(interval);
		setInterval(() => updateTime(), 300);
	}
</script>

<g class={`zone ${className}`}>
	<text x="50%" y="30" font-size="36" class="clock" text-anchor="middle" dominant-baseline="text-top">{clock}</text>
	<text x="50%" y="60" font-size="28" class="label" text-anchor="middle" dominant-baseline="text-top">{label}</text>
</g>

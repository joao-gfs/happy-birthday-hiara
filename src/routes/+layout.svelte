<script lang="ts">
    import { base } from '$app/paths';
	import './layout.css';

	let { children } = $props();
</script>

<svelte:head>
    <link rel="icon" href={`${base}/images/favicon.ico`} />
    <title>Feliz aniversário!</title>
</svelte:head>
<div>
    {@render children()}
</div>

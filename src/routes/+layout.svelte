<script lang="ts">
	import "../app.css";
	import favicon from "$lib/assets/favicon.svg";

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav class="navbar bg-base-100 shadow-sm">
	<a class="btn btn-accent text-xl" href="/">Home</a>
	<!-- <a class="btn btn-ghost btn-primary text-xl" href="/reference">Reference</a> -->
</nav>

{@render children()}

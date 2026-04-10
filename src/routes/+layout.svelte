<script lang="ts">
	import "../app.css";
	import favicon from "$lib/assets/favicon.svg";
    import { page } from "$app/state";

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav class="navbar bg-base-100 shadow-sm">
	<a class="btn btn-ghost btn-primary text-xl" href="/" class:active={page.url.pathname === '/'}>Home</a>
	<a class="btn btn-ghost btn-primary text-xl" href="/borrowedTime" class:active={page.url.pathname === '/borrowedTime'}>Borrowed Time</a>
	<a class="btn btn-ghost btn-primary text-xl" href="/stchr" class:active={page.url.pathname === '/stchr'}>STCHr</a>
</nav>

{@render children()}

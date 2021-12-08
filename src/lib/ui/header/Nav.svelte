<script lang="ts">
	import Logo from '$lib/ui/Logo.svelte'
	import { page } from '$app/stores'

	const links = ['templates', 'components', 'tools', 'guides', 'cheat sheet', 'events']

	export let scrolled = false
</script>

<template lang="pug">

	nav
		ul
			+each('links as link, i')

				li(class:active='{$page.path === `/${link}`}')

					a(
						sveltekit:prefetch
						href=`/${link}`
						class:scrolled
					) {link}

</template>

<style lang="scss">
	nav {
		display: flex;
		justify-content: center;

		width: 100%;
		max-width: 65vw;
		margin: 0 auto;

		contain: content;
	}

	ul {
		display: flex;
		justify-content: space-around;
		gap: 2rem;
		flex-wrap: wrap;

		width: 100%;

		z-index: 1;
	}

	li {
		list-style: none;
	}

	nav a {
		display: flex;
		justify-content: center;
		align-items: center;

		height: 100%;
		min-height: 150%;

		&.scrolled {
			min-height: 100%;
		}

		color: var(--dark-a);

		font-size: 1rem;
		font-weight: 700;
		text-transform: uppercase;
		text-decoration: none;
		letter-spacing: 10%;

		transition: min-height 0.5s;
	}

	a:hover {
		color: var(--svelte);
	}
</style>

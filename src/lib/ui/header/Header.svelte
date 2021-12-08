<script lang="ts">
	import { ThemeToggle, scrollY } from 'fractils'
	import Logo from '$lib/ui/Logo.svelte'
	import Nav from './Nav.svelte'

	$: scrolled = $scrollY > 100
</script>

<template lang="pug">

	header
		.header-bg(class:scrolled)

		.corner#home(class:scrolled)
			a(href='/')
				Logo

		Nav(bind:scrolled)

		#theme.corner
			ThemeToggle

</template>

<style lang="scss">
	#home {
		left: 3px;

		height: 100px;
		width: 100px;
		padding: 10px;

		transition: transform 0.5s;
		transform-origin: top left;

		&.scrolled {
			transform: scale(0.35);
		}
	}

	header {
		display: flex;
		justify-content: space-between;
		position: fixed;
		top: 0;

		width: 100vw;
		height: 2.5rem;

		z-index: 50;

		& .header-bg {
			position: absolute;

			width: 100%;
			height: 0px;
			min-height: 0px;

			background: rgba(var(--light-a-rgb), 1);

			transition: 0.5s;

			&.scrolled {
				min-height: 40px;
			}
		}
	}

	.corner {
		display: flex;
		align-items: center;
		position: fixed;
		top: 3px;

		width: 2rem;
	}

	#theme {
		right: 0;
	}

	:global(#theme .icon) {
		font-size: 1.25rem;
	}
</style>

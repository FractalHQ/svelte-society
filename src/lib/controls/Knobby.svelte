<script lang="ts" context="module">
	import { writable, derived } from 'svelte/store'
	import type { Writable } from 'svelte/store'
	import * as knobby from 'svelte-knobby'
	import { themes } from '$lib/theme'
	import { theme } from 'fractils'

	type theme = 'a' | 'b' | 'c'
	export const activeTheme: Writable<theme> = writable('a')

	export const controls = knobby.panel({
		title: 'Svelte Society',
		color: '#ff3e00',
		A: (value: theme) => {
			activeTheme.set('a')
		},
		B: (value: theme) => {
			activeTheme.set('b')
		},
		themes
	})

	export const style = derived(
		[controls, activeTheme, theme],
		([$controls, $activeTheme, $theme]) => {
			return `
		--svelte: ${$controls?.color};
		--brand-a: ${$controls?.themes[$activeTheme][$theme].brandA};
		--brand-b: ${$controls?.themes[$activeTheme][$theme].brandB};
		--brand-c: ${$controls?.themes[$activeTheme][$theme].brandC};
		--brand-d: ${$controls?.themes[$activeTheme][$theme].brandD};
		--brand-e: ${$controls?.themes[$activeTheme][$theme].brandE};
		`
		}
	)
</script>

<style lang="scss">
	:global(:root[theme='dark'] .knobby) {
		--convex: #151414 !important;
		--concave: #151414 !important;
		--light: #3d3d3d !important;
		--dark: #0b0a0a !important;
		--bg: #151414 !important;
		--fg: white !important;
		--flash: unset;

		background: #232328 !important;
	}
	:global(:root[theme='dark'] .knobby input:not([type])) {
		color: white !important;
	}
	:global(.knobby .content::-webkit-scrollbar) {
		visibility: hidden;

		width: 0 !important;
	}
</style>

<script lang="ts">
	import type { SvelteComponent } from 'svelte'
	import type { Writable } from 'svelte/store'
	import { browser, dev } from '$app/env'

	let panel: typeof SvelteComponent | null = null
	export let controls: Writable<any> | null = null,
		style: string | null = null
	;(async function init() {
		if (dev && browser) {
			panel = (await import('./Knobby.svelte')).default
		}
	})()
</script>

<template lang="pug">

		+if('panel')
			svelte:component(this='{panel}' bind:controls bind:style)

</template>

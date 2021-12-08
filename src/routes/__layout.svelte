<script lang="ts">
	import { style, Controls } from '$lib/controls'
	import { Fractils } from 'fractils'
	import { page } from '$app/stores'
	import { Header } from '$lib/ui'
	import 'greset/css/greset.css'
	import '../styles/app.scss'

	const pageTitle = (path: string) => {
		if (path === '/') return 'Home'
		const title = path.split('/')[1]
		return title.charAt(0).toUpperCase() + title.slice(1)
	}
</script>

<template lang="pug">

	Fractils

	svelte:head
		title {pageTitle($page.path)} · Svelte Society

	Header

	span(style='{$style}')
		slot

	Controls

</template>

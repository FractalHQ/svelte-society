<script lang="ts">
	import { controls } from '$lib/controls'
</script>

<template lang="pug">
	
	.page

		.title
			h1 {$controls?.title}

			svg.underline(width='100%' height='100%' viewBox='0 0 100 5')
				path(d='M1,1 v5,0 h100,3 v-1,-1 z')


		section.about
			p A global network of Svelte fans that strive to promote 
				a(href='https://svelte.dev' target='blank') Svelte
				|  and its ecosystem.
		
		.spacer
		
		h2 Join the Community
		section.join
			p If you want to reach out to us or find like-minded people from around the world you can check out the resources below 👇

</template>

<style lang="scss">
	.page {
		display: flex;
		flex-direction: column;
		flex-grow: 1;

		// TODO: remove this
		min-height: 300vh;

		background-color: var(--brand-c);
	}

	.title {
		position: relative;

		width: fit-content;
		height: fit-content;
		margin: 5rem auto 0 auto;
		padding-top: 10rem;

		& h1 {
			position: relative;

			font-family: var(--font-secondary);
			font-size: 4rem;
			font-variation-settings: 'wght' 600;

			z-index: 2;

			transform-style: preserve-3d;
		}

		& svg {
			fill: var(--svelte);

			transform: rotate(-3deg) translateY(-1rem);
		}
	}

	section {
		max-width: 800px;
		margin: 0 auto;

		border-radius: 4px;

		&.about {
			margin-top: 3rem;

			background: rgba(var(--light-a-rgb), 0.5);

			& p {
				padding: 1rem;

				box-shadow: var(--shadow-sm);
			}
		}

		&.join {
			& p {
				margin-top: 3rem;
			}
		}
	}

	h2 {
		margin: 5rem auto 0 auto;

		font-size: 2.5rem;
	}

	.spacer {
		height: 10rem;
	}
</style>

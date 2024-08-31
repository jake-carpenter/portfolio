<script>
	import Mastodon from '$lib/icons/socials/mastodon.svelte';
	import FeaturesIcon from '$lib/icons/features.svelte';
	import GitHubIcon from '$lib/icons/socials/github.svelte';
	import Button from '$lib/components/atoms/Button.svelte';
	import Sparkles from '../atoms/Sparkles.svelte';
</script>

<section id="hero">
	<h1 class="hello">Welcome to my blog!</h1>
	<p class="intro">
		<span class="left">It's all pretty much a template right now</span>
	</p>
	<div class="ctas">
		<Sparkles>
			<Button href="https://github.com/jake-carpenter">
				<GitHubIcon slot="icon" />
				Github
			</Button>
		</Sparkles>
		<Button color="primary" href="https://hachyderm.io/@jakecarpenter">
			<Mastodon slot="icon" />
			Find me on Mastodon
		</Button>
	</div>
</section>

<style lang="scss">
	@import '$lib/scss/breakpoints.scss';

	#hero {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 15px;
		position: relative;
		padding: 80px 0;

		@include for-phone-only {
			padding: 40px 0 50px;
		}

		.hello {
			text-align: center;
		}

		.intro {
			font-weight: 500;
			font-size: 1.4rem;
			width: min(100%, 500px);
			display: flex;
			flex-direction: column;

			.left {
				text-align: left;
			}
			.right {
				text-align: right;
			}

			@include for-phone-only {
				display: none;
			}
		}

		.ctas {
			display: flex;
			flex-wrap: wrap;
			align-items: center;
			justify-content: center;
			gap: 10px;
			width: 100%;
		}
	}
</style>

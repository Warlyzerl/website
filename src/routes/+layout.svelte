<script lang="ts">
	import '../app.pcss';
	import '../styles/global.css';
	import { AppBar, ListBox, ListBoxItem, popup, storePopup } from '@skeletonlabs/skeleton';
	import type { PopupSettings } from '@skeletonlabs/skeleton';
	import { computePosition, autoUpdate, offset, shift, flip, arrow } from '@floating-ui/dom';

	storePopup.set({ computePosition, autoUpdate, offset, shift, flip, arrow });
	const popupCombobox: PopupSettings = {
		event: 'click',
		target: 'popupCombobox',
		placement: 'bottom',
		closeQuery: '.listbox-item'
	};

	function navigateToTarotCards() {
      var targetPage = "/cards";
      window.location.href = targetPage;
	}
</script>

<header class="font-heading-token header-text ">
	<AppBar background="bg-secondary-100 text-primary-600" padding="header-padding">
		<div slot="lead" class="lead">
			<a class="lead" href="/"><img class="pochita" src="/pochita.png" alt="Pochita"> Home</a>
			<a class="btn-icon hover:variant-soft-secondary" href="https://github.com/warlyzerl"><img class="socials" src="/github.png" alt="Github"></a>
			<a class="btn-icon hover:variant-soft-secondary" href="https://www.linkedin.com/in/willie-zeng/"><img class="socials" src="/linkedin.png" alt="LinkedIn"></a>
		</div>
		<div class="links" slot="trail">
			<a class="btn variant-filled-primary" href="/about">About</a>
			<button class="btn variant-filled-tertiary" use:popup={popupCombobox}>Projects</button>
		</div>
	</AppBar>
	<div class="card w-48 shadow-xl py-2" data-popup="popupCombobox">
		<ListBox rounded="rounded-none">
			<ListBoxItem on:click={navigateToTarotCards} name="medium" value="books">Tarot Cards</ListBoxItem>
		</ListBox>
		<div class="arrow bg-surface-100-800-token" />
	</div>
</header>
<main>
	<slot />
</main>
<footer>
	<p>5'11" 193lbs</p>
</footer>

<style>
	.socials {
		max-width: 30px;
	}

	.header-text{
		font-size: larger;
	}

	.lead {
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.pochita {
		max-width: 60px;
		max-height: auto;
		margin-right: 10px;
	}
	header {
		text-align: center;
	}
	main {
		max-width: 960px;
		margin: 20px auto;
	}
	footer {
		text-align: center;
	}
	.links {
		margin-right: 10px;
		margin-left: auto;
	}
	a {
		margin-left: 10px;
	}
</style>
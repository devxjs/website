<template>
	<BaseContainer>
		<nav>
			<ul>
				<li class="logo">
					<a href="/tv"><img src="~/assets/svg/logo-tv-white.svg" alt="Directus TV" /></a>
				</li>
				<li><NuxtLink href="/">Website</NuxtLink></li>
				<li><a href="https://docs.directus.io">Docs</a></li>
				<li><NuxtLink href="/demo">Book a Demo</NuxtLink></li>
			</ul>
			<BaseButton
				label="Subscribe"
				class="subscribe"
				:class="buttonClass"
				type="button"
				color="white"
				size="large"
				outline
				icon-start="account_circle"
				@click="openModal"
			/>
		</nav>
	</BaseContainer>
	<dialog ref="modal">
		<div class="nav">
			<p>Never miss an episode</p>
			<BaseIcon class="close" name="close" size="small" @click="closeModal" />
		</div>
		<p>We'll let you know when we drop new episodes and shows directly in your inbox.</p>
		<BaseHsForm form-id="f8d7d0dd-33a7-4d28-8f14-b50d7c806ee7" />
	</dialog>
</template>

<script setup>
const modal = ref(null);

defineProps({
	buttonClass: String,
});

const openModal = () => modal.value.showModal();
const closeModal = () => modal.value.close();
</script>

<style lang="scss" scoped>
nav {
	display: flex;
	justify-content: space-between;
	padding: 1em 0;
	ul {
		padding-left: 0;
		list-style-type: none;
		display: flex;
		align-items: center;
		gap: 3em;
		margin: 0;
		li {
			img {
				height: 2rem;
			}
			a {
				color: white;
				text-decoration: none;
			}
			&:not(.logo) {
				display: none;
			}
		}
	}
	.subscribe {
		--background-color: white;
		margin: 1rem 0;
	}
}

dialog {
	width: 300px;
	background: var(--primary-900);
	border: 1px solid var(--primary-400);
	border-radius: var(--rounded-lg);
	padding-top: 20px;
	&::backdrop {
		background: rgba(0, 0, 0, 0.5);
	}
	.nav {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		p {
			font-weight: bold;
			color: var(--primary-400);
		}
		.close {
			cursor: pointer;
			color: var(--primary-400);
		}
	}
	> p {
		margin: 1rem 0;
	}
}

@media (width > 60rem) {
	nav ul {
		li img {
			height: 3rem;
		}
		li:not(.logo) {
			display: block;
		}
	}
}
</style>

<style lang="scss">
body.tv .hs-form .actions input[type='submit'] {
	margin-block-start: var(--space-4);
	background: var(--primary-400);
	color: white;
	border: none;
	&:hover {
		background: var(--primary-200);
	}
}
</style>

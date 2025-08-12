<script>
	import '/src/css/index.css';

	import config from '/src/config';
	import Logo from '$lib/Logo.svelte';

	import PageLoader from './PageLoader.svelte';

	let { data, children } = $props();
</script>

<svelte:head>
	<link rel="icon" type="image/svg+xml" href="/favicon.svg" />
	<link rel="alternate" type="application/rss+xml" title="RSS" href="/feed.xml" />
</svelte:head>

<PageLoader />

<div class="max-w-container mx-auto flex min-h-dvh flex-col">
	<header class="flex flex-row px-4 py-8 md:p-8">
		<figure>
			<a class="flex flex-row items-center gap-4" href="/" title={config.siteTitle}>
				<Logo />
			</a>
		</figure>
	</header>

	<main class="flex-1">
		{@render children()}
	</main>

	<footer class="mt-8">
		<nav class="py-4 text-xl md:p-4">
			<ul class="flex flex-row flex-wrap gap-x-6 p-2">
				<li><a class="flex flex-row gap-0.5 p-2 underline" href="/feed.xml">RSS</a></li>
				{#each data.pages as item (item.id)}
					<li><a class="block p-2 underline" href="/{item.id}">{item.title}</a></li>
				{/each}
				<li>
					<a
						class="flex flex-row gap-0.5 p-2"
						href="https://github.com/zespere"
						target="_blank"
						rel="external noreferrer nofollow"
						><span class="underline">Github</span><span class="text-current/20">&#8599;</span></a
					>
				</li>
				<li>
					<a
						class="flex flex-row gap-0.5 p-2"
						href="https://bsky.app/profile/wniak.com"
						target="_blank"
						rel="external noreferrer nofollow"
						><span class="underline">Bluesky</span><span class="text-current/20">&#8599;</span></a
					>
				</li>
			</ul>
		</nav>

		<div class="copy px-4 py-8 text-xl md:p-8 border-t">
			<p class="text-center">
				&copy; {new Date().getFullYear()} Wojciech Woźniak
			</p>
		</div>
	</footer>
</div>

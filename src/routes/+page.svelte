<script lang="ts">
	import Button from '$lib/component/Button.svelte';
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';

	import Image from '../assets/hero-section-image.png?enhanced';
	import Projects from '$lib/sections/Projects.svelte';
	import Skills from '$lib/sections/Skills.svelte';
	import About from '$lib/sections/About.svelte';

	let loaded = false;

	let opened = false;

	$: pages = ['projects', 'skills', 'about'];
	const onPage = (page: string) => pages[0] == page;

	const selectPage = (option: string) => {
		const [, rest] = pages.filter((e) => e != option);
		opened = false;
		setTimeout(() => {
			pages = [option, ...rest];
			opened = true;
		}, 500);
	};

	onMount(() => {
		setTimeout(() => {
			opened = true;
			loaded = true;
		}, 1000);
	});
</script>

<div class="h-screen overflow-clip">
	<div
		class="flex justify-center place-items-center {opened
			? 'h-[60vh]'
			: 'h-screen'} transition-all duration-500 gap-32"
	>
		<div class="flex flex-col gap-2">
			<div class="py-14"></div>
			<h1 class="px-1 text-2xl font-medium">Joshua Hunter</h1>
			<h3 class="px-1 text-xl">Full Stack Developer</h3>
			<div class="flex gap-3">
				<Button on:click={() => location.href = 'mailto:koficenti@gmail.com'} text="Contact Me" Extra="text-white mt-3 text-sm" />
				<Button on:click={() => location.href = 'https://github.com/koficenti'}
					text="View Github"
					Style="bg-slate-900"
					HoverStyle="bg-slate-800"
					Extra="text-white mt-3 text-sm"
				/>
			</div>
		</div>
		<div>
			{#key pages}
				<div class="flex justify-end gap-5 mb-5">
					<Button
						on:click={() => selectPage('projects')}
						text="Projects"
						Style="bg-white {opened && onPage('projects') ? 'ring ring-blue-300' : ''}"
						HoverStyle="bg-gray-50 {opened && onPage('projects') ? 'ring ring-blue-300' : ''}"
						LessRound={true}
					/>
					<Button
						on:click={() => selectPage('skills')}
						text="Skills"
						Style="bg-white {opened && onPage('skills') ? 'ring ring-blue-300' : ''}"
						HoverStyle="bg-gray-50 {opened && onPage('skills') ? 'ring ring-blue-300' : ''}"
						LessRound={true}
					/>
					<Button
						on:click={() => selectPage('about')}
						text="About me"
						Style="bg-white {opened && onPage('about') ? 'ring ring-blue-300' : ''}"
						HoverStyle="bg-gray-50 {opened && onPage('about') ? 'ring ring-blue-300' : ''}"
						LessRound={true}
					/>
				</div>
				<div class="relative w-[720px] aspect-video bg-white shadow-md rounded-2xl overflow-clip" id="main">
					{#key pages}
						{#if opened && onPage('about')}
							<div transition:fade class="absolute w-full h-full px-20 text-center mt-[45%] translate-y-[-50%]">
								<h1 class="font-medium text-lg">
								Hello my name is Josh! 👋
								</h1>
								<p class="mt-5">
									🚀 I'm a full stack developer passionate about everything tech. My expertise lies in web technologies such as laravel, react, django but also I'm familiar with other stuff such as app development.
								</p>
								<p class="mt-5">
									💼 Currently looking for work so please reach out if you need a helping hand.
								</p>
							</div>
							<div transition:fade>
								<div class="goodbye-image">
									<enhanced:img alt="Hero Section Image" src={Image} />
								</div>
							</div>
						{:else}
							<div>
								<enhanced:img alt="Hero Section Image" src={Image} />
							</div>
						{/if}
					{/key}
				</div>
			{/key}
		</div>
	</div>
	{#key pages}
		{#if opened && onPage('projects')}
			<Projects />
		{/if}
		{#if opened && onPage('skills')}
			<Skills />
		{/if}
		{#if opened && onPage('about')}
			<About />
		{/if}
	{/key}
</div>

<style>
	@keyframes Goodbye-Image {
		from {
			opacity: 1;
		}
		to {
			opacity: 0;
		}
	}
	.goodbye-image {
		pointer-events: none;
		animation: 0.5s Goodbye-Image ease forwards;
	}
</style>

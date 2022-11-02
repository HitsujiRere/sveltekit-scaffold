<script lang="ts">
	import { onMount } from 'svelte';

	let theme: 'light' | 'dark' | null = null;

	$: {
		if (typeof localStorage !== 'undefined' && theme) {
			localStorage.theme = theme;
		}

		if (typeof document !== 'undefined') {
			if (theme === 'dark') {
				document.documentElement.classList.add('dark');
			} else if (theme === 'light') {
				document.documentElement.classList.remove('dark');
			}
		}
	}

	onMount(() => {
		theme = document.documentElement.classList.contains('dark') ? 'dark' : 'light';
	});

	const toggleTheme = () => {
		theme = theme === 'light' ? 'dark' : 'light';
	};
</script>

<header class="sticky top-0 bg-white p-4 dark:bg-gray-900">
	<div class="mx-auto flex max-w-screen-lg items-center justify-between">
		<div>
			<a
				href="/"
				class="text-2xl font-bold text-gray-800 hover:text-green-500 dark:text-white dark:hover:text-green-500"
			>
				Svelte
			</a>
		</div>
		<div>
			<ul class="flex items-center gap-x-8">
				<li>
					<a
						href="/"
						class="font-medium text-gray-700 hover:text-green-500 dark:text-gray-400 dark:hover:text-green-500"
					>
						AAA
					</a>
				</li>
				<li>
					<a
						href="/"
						class="font-medium text-gray-700 hover:text-green-500 dark:text-gray-400 dark:hover:text-green-500"
					>
						BBB
					</a>
				</li>
				<li>
					<a
						href="/"
						class="font-medium text-gray-700 hover:text-green-500 dark:text-gray-400 dark:hover:text-green-500"
					>
						CCC
					</a>
				</li>
				<button
					type="button"
					class="rounded p-1 text-gray-700 hover:bg-gray-100 dark:text-gray-400 dark:hover:bg-gray-700"
					on:click={toggleTheme}
				>
					{#if theme === 'light'}
						<svg
							class="h-6 w-6"
							fill="currentColor"
							viewBox="0 0 20 20"
							xmlns="http://www.w3.org/2000/svg"
						>
							<path
								fill-rule="evenodd"
								d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z"
								clip-rule="evenodd"
							/>
						</svg>
					{/if}
					{#if theme === 'dark'}
						<svg
							class="h-6 w-6"
							fill="currentColor"
							viewBox="0 0 20 20"
							xmlns="http://www.w3.org/2000/svg"
							><path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z" /></svg
						>
					{/if}
				</button>
			</ul>
		</div>
	</div>
</header>

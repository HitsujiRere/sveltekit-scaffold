<script>
	import '../app.postcss';
	import Header from './Header.svelte';
</script>

<div class="min-h-screen bg-white dark:bg-gray-900 dark:[color-scheme:dark]">
	<Header />
	<slot />
</div>

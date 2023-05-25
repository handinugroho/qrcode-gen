<script>
	import '@skeletonlabs/skeleton/themes/theme-rocket.css';
	// This contains the bulk of Skeletons required styles:
	// NOTE: this will be renamed skeleton.css in the v2.x release.
	import '@skeletonlabs/skeleton/styles/skeleton.css';

	// Finally, your application's global stylesheet (sometimes labeled 'app.css')
	import '../app.postcss';

	import { Toast } from '@skeletonlabs/skeleton';
</script>

<slot />

<svelte:head>
	<title>QR Code Generator</title>
</svelte:head>

<Toast position="tr" />

<script lang="ts">
	import QRCode from 'qrcode';
	import { toastStore } from '@skeletonlabs/skeleton';
	import type { ToastSettings } from '@skeletonlabs/skeleton';

	let input: HTMLInputElement;
	let inputUrl = '';

	let canvas: HTMLCanvasElement;

	function handleClick() {
		if (inputUrl.length == 0) {
			const t: ToastSettings = {
				message: 'Input URL must be entered!',
				background: 'variant-filled-error'
			};
			toastStore.trigger(t);
			input.focus();
			return;
		}
		QRCode.toCanvas(
			canvas,
			inputUrl,
			{
				errorCorrectionLevel: 'H',
				width: 240
			},
			function (error) {
				if (error) {
					const t: ToastSettings = {
						message: error.message,
						background: 'variant-filled-error'
					};
					toastStore.trigger(t);
				}
			}
		);
	}
</script>

<div class="mx-auto max-w-3xl my-48">
	<h1 class="h1">QR Code Generator</h1>
	<div class="mt-10 space-y-10">
		<label class="label">
			<span>URL Input</span>
			<input
				class="input"
				type="text"
				placeholder="https://yourwebsite.url"
				bind:this={input}
				bind:value={inputUrl}
			/>
		</label>
		<button type="button" class="btn variant-filled" on:click={handleClick}>Generate</button>
		<div class="">
			<h4 class="h4 mb-3">Result</h4>
			<canvas id="canvas" bind:this={canvas} />
		</div>
	</div>
</div>

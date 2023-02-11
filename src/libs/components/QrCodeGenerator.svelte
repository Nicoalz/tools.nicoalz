<script>
	import QRCode from 'qrcode-generator';
	let qrCodeImage = '';
	let isQRGenerated = false;
	function generateQRCode() {
		isQRGenerated = false;
		let qrcode = QRCode(0, 'L');
		qrcode.addData(inputText);
		qrcode.make();
		const imageData = qrcode.createDataURL(10, 10);
		qrCodeImage = imageData;
		isQRGenerated = true;
	}

	let inputText = '';
</script>

<div class="flex flex-col items-center justify-center w-full">
	<div class="flex flex-col items-center w-full">
		<input
			type="text"
			class="w-full p-4 border-gray-300 border-b-4 rounded focus:outline-none focus:border-gray-400"
			placeholder="Enter your text here..."
			bind:value={inputText}
		/>
		<div class="flex w-full justify-start">
			<button
				class="btn-violet text-xs"
				on:click={() => {
					navigator.clipboard.readText().then((text) => {
						inputText = text;
					});
				}}>Paste</button
			>
		</div>
		<button class="btn-blue mb-8" on:click={generateQRCode}> Generate QR Code </button>
		{#if isQRGenerated}
			<img class="w-64 h-64" src={qrCodeImage} alt="QR code" />
		{/if}
	</div>
</div>

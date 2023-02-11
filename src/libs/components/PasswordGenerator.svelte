<script>
	import { onMount } from 'svelte';
	import TiArrowSync from 'svelte-icons/ti/TiArrowSync.svelte';
	import Copy from './Copy.svelte';

	onMount(() => {
		generatePassword();
	});

	let generatedPassword = '';
	let isLetters = true;
	let isNumbers = true;
	let isSymbols = true;
	let length = 16;

	function generatePassword() {
		const letters = 'abcdefghijklmnopqrstuvwxyz';
		const numbers = '0123456789';
		const symbols = '!@#$%^&*()_+~`|}{[]:;?><,./-=';
		let characters = '';
		if (isLetters) {
			characters += letters;
		}
		if (isNumbers) {
			characters += numbers;
		}
		if (isSymbols) {
			characters += symbols;
		}
		let password = '';
		for (let i = 0; i < length; i++) {
			password += characters.charAt(Math.floor(Math.random() * characters.length));
		}
		generatedPassword = password;
	}
</script>

<div class="flex flex-col items-center justify-center w-full">
	<div class="flex flex-col items-center w-full">
		<div
			class="mb-1 p-4 text-black bg-white border-gray border-b-4 w-full flex justify-start"
		>
			<button
				id="reroll"
				class=" h-6 w-6 transition duration-500 ease-in-out transform mr-10"
				on:click={() => {
					document.getElementById('reroll').classList.toggle('rotate-180');
					generatePassword();
				}}
			>
				<TiArrowSync />
			</button>
			<p>{generatedPassword || 'Choose at least one option'}</p>
		</div>
		<div class="flex w-full justify-start items-center">
			<Copy text={generatedPassword} />
		</div>
		<div class="flex flex-col items-center w-full ">
			<p class="mb-4">Choose your options:</p>
			<div class="flex flex-col">
				<div class="mb-4">
					<p class={`${length < 10 && 'text-red-500'}`}>Length: {length}</p>
					<input
						class={`w-full ${length < 10 && 'accent-red-500'}`}
						type="range"
						min="5"
						max="40"
						step="1"
						bind:value={length}
						on:change={generatePassword}
					/>
				</div>
				<div class="flex flex-wrap">
					<div>
						<input
							class="hidden"
							type="checkbox"
							id="letters"
							bind:checked={isLetters}
							on:change={generatePassword}
						/>
						<label class={`cursor-pointer ${isLetters ? 'btn-blue' : 'btn-gray'}`} for="letters"
							>Letters</label
						>
					</div>
					<div>
						<input
							class="hidden"
							type="checkbox"
							id="numbers"
							bind:checked={isNumbers}
							on:change={generatePassword}
						/>
						<label class={`cursor-pointer ${isNumbers ? 'btn-blue' : 'btn-gray'}`} for="numbers"
							>Numbers</label
						>
					</div>
					<div>
						<input
							class="hidden"
							type="checkbox"
							id="symbols"
							bind:checked={isSymbols}
							on:change={generatePassword}
						/>
						<label class={`cursor-pointer ${isSymbols ? 'btn-blue' : 'btn-gray'}`} for="symbols"
							>Symbols</label
						>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>

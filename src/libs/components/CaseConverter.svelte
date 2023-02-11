<script>
	import Copy from './Copy.svelte';
	let inputText = '';
	let orignalText = '';
	function toCamelCase(str) {
		return str
			.replace(/(?:^\w|[A-Z]|\b\w)/g, function (word, index) {
				return index === 0 ? word.toLowerCase() : word.toUpperCase();
			})
			.replace(/\s+/g, '');
	}

	function toPascalCase(str) {
		return str
			.replace(/(?:^\w|[A-Z]|\b\w)/g, function (word, index) {
				return word.toUpperCase();
			})
			.replace(/\s+/g, '');
	}

	function toSnakeCase(str) {
		return str
			.replace(/(?:^\w|[A-Z]|\b\w)/g, function (word, index) {
				return index === 0 ? word.toLowerCase() : word.toUpperCase();
			})
			.replace(/\s+/g, '_');
	}

	function toKebabCase(str) {
		return str
			.replace(/(?:^\w|[A-Z]|\b\w)/g, function (word, index) {
				return index === 0 ? word.toLowerCase() : word.toUpperCase();
			})
			.replace(/\s+/g, '-');
	}

	function saveOriginalText() {
		orignalText = inputText;
	}

	function toOriginalCase() {
		inputText = orignalText;
	}
</script>

<div class="flex flex-col items-center justify-center w-full">
	<div class="flex flex-col items-center w-full">
		<textarea
			class="w-full mb-1 h-48 p-2 border-gray-300 border-b-4 resize-none rounded focus:outline-none focus:border-gray-400"
			placeholder="Enter your text here..."
			bind:value={inputText}
			on:input={saveOriginalText}
		/>
		<div class="flex w-full flex-start items-center">
			<Copy text={inputText} />
			<button
				class="btn-violet text-xs"
				on:click={() => {
					navigator.clipboard.readText().then((text) => {
						inputText = text;
					});
					saveOriginalText();
				}}>Paste</button
			>
		</div>
		<div class="flex flex-col items-center w-full">
			<p class="mb-2">Choose your case type:</p>
			<div>
				<button
					class="btn-blue"
					on:click={() => {
						toOriginalCase();
					}}
				>
					Original
				</button>
				<button
					class="btn-blue"
					on:click={() => {
						inputText = inputText.toLowerCase();
					}}
				>
					lowercase
				</button>
				<button
					class="btn-blue"
					on:click={() => {
						inputText = inputText.toUpperCase();
					}}
				>
					UPPERCASE
				</button>
				<button
					class="btn-blue"
					on:click={() => {
						inputText = toCamelCase(inputText);
					}}
				>
					camelCase
				</button>
				<button
					class="btn-blue"
					on:click={() => {
						inputText = toPascalCase(inputText);
					}}
				>
					PascalCase
				</button>
				<button
					class="btn-blue"
					on:click={() => {
						inputText = toSnakeCase(inputText);
					}}
				>
					snake_case
				</button>
				<button
					class="btn-blue"
					on:click={() => {
						inputText = toKebabCase(inputText);
					}}
				>
					kebab-case
				</button>
			</div>
		</div>
	</div>
</div>

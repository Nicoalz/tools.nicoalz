<script>
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

	function copyToClipboard() {
		navigator.clipboard.writeText(inputText);
	}
</script>

<div class="flex flex-col items-center justify-center w-full">
	<div class="flex flex-col items-start w-full">
		<p class="mb-4">Enter your text below:</p>
		<textarea
			class="w-full h-32 p-2 border border-gray-300 rounded"
			placeholder="Enter your text here..."
			bind:value={inputText}
			on:input={saveOriginalText}
		/>
		<div class="flex flex-col items-start w-full ">
			<p>
				Choose your case type: <span class="font-italic text-xs text-gray-500"
					>(automatically copied to clipboard)
				</span>
			</p>
			<div>
				<button
					class="btn-case"
					on:click={() => {
						toOriginalCase();
						copyToClipboard();
					}}
				>
					Original
				</button>
				<button
					class="btn-case"
					on:click={() => {
						inputText = inputText.toLowerCase();
						copyToClipboard();
					}}
				>
					lowercase
				</button>
				<button
					class="btn-case"
					on:click={() => {
						inputText = inputText.toUpperCase();
						copyToClipboard();
					}}
				>
					UPPERCASE
				</button>
				<button
					class="btn-case"
					on:click={() => {
						inputText = toCamelCase(inputText);
						copyToClipboard();
					}}
				>
					camelCase
				</button>
				<button
					class="btn-case"
					on:click={() => {
						inputText = toPascalCase(inputText);
						copyToClipboard();
					}}
				>
					PascalCase
				</button>
				<button
					class="btn-case"
					on:click={() => {
						inputText = toSnakeCase(inputText);
						copyToClipboard();
					}}
				>
					snake_case
				</button>
				<button
					class="btn-case"
					on:click={() => {
						inputText = toKebabCase(inputText);
						copyToClipboard();
					}}
				>
					kebab-case
				</button>
			</div>
		</div>
	</div>
</div>

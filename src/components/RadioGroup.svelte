<script lang="ts">
	import { getContext, onMount } from 'svelte';
	import type { QuizContext } from '../types';

	let { name, options, correctAnswer, isSubmitted } = $props();

	let selectedOption: string | null = $state(null);

	const { incrementCount, incrementCorrect } = getContext<QuizContext>('incrementCount');
	// Function to check if the selected answer is correct
	onMount(() => {
		incrementCount();
	});
</script>

<fieldset
	class="mt-12 flex flex-col gap-4 rounded-md border border-slate-900 bg-slate-300 p-4 dark:border-slate-200 dark:bg-slate-950"
>
	<legend class="text-2xl font-bold">{name}</legend>
	{#each options as option}
		<label>
			<input type="radio" required {name} value={option} bind:group={selectedOption} />
			{option}
		</label>
	{/each}
</fieldset>

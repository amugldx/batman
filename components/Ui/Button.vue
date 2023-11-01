<script setup lang="ts">
	import { cva } from 'class-variance-authority';
	import { twMerge } from 'tailwind-merge';

	const buttonClass = computed(() => {
		return twMerge(
			cva('px-4 py-1 rounded-md flex justify-center items-center transition-all', {
				variants: {
					intent: {
						primary:
							'bg-black dark:bg-white text-white dark:text-black hover:bg-slate-800 dark:hover:bg-slate-100 focus:bg-slate-800 dark:focus:bg-slate-100',
						secondary: 'bg-purple-600 text-white hover:bg-purple-500',
						ghost: 'dark:text-white text-black',
					},
					disabled: {
						true: '',
					},
					loading: {
						true: '',
					},
				},
				compoundVariants: [
					{
						intent: ['primary', 'secondary', 'ghost'],
						disabled: true,
						class: 'disabled:cursor-not-allowed',
					},
					{
						intent: ['primary', 'secondary', 'ghost'],
						disabled: true,
						loading: true,
						class: 'cursor-not-allowed',
					},
				],
			})({
				intent: intent,
				disabled: disable,
				loading: loading,
			}),
		);
	});

	const {
		intent = 'primary',
		type,
		loading,
		disable = false,
	} = defineProps<{
		intent: 'primary' | 'secondary' | 'ghost';
		type?: 'submit';
		disable?: boolean;
		loading?: boolean;
	}>();

	defineEmits(['onClick']);
</script>

<template>
	<div>
		<button
			@click="$emit('onClick')"
			:class="buttonClass"
			:type="type"
			:disabled="disable"
			><span v-if="loading"
				><Icon
					name="tdesign:loading"
					class="animate-spin"
					size="20px"
			/></span>
			<slot v-else />
		</button>
	</div>
</template>

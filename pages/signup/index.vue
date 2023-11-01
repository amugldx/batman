<script setup lang="ts"></script>

<template>
	<div class="flex flex-col items-center justify-center mt-20">
		<UiInput />
		<UiButton intent="primary">Click</UiButton>
		<UiButton
			intent="primary"
			:disable="true"
			>Click</UiButton
		>
		<UiButton intent="secondary">Click</UiButton>
		<UiButton
			intent="secondary"
			:loading="true"
			>Click</UiButton
		>
		<UiButton intent="ghost">Click</UiButton>
		<UiButton
			intent="ghost"
			:loading="true"
			:disable="true"
			>Click</UiButton
		>
	</div>
</template>

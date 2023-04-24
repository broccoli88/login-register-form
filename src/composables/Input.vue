<template>
	<div class="input-container">
		<label for="username">
			<slot></slot>
		</label>
		<input type="text" name="username" class="input" />
	</div>
</template>
<style scoped>
	.input-container {
		margin-top: 2rem;
	}

	.input {
		display: block;
		width: 100%;

		margin-top: 0.7rem;
		padding: 1rem 2rem;
		font-size: 1.5rem;
		color: var(--color-text);
		border: none;
		border-radius: 5px;
		background: hsl(43, 74%, 66%, 0.5);
		box-shadow: 0 0 10px var(--box-shadow);
		outline: none;
	}
</style>

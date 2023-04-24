<template>
	<button type="submit" class="btn">
		<slot></slot>
	</button>
</template>
<style scoped>
	.btn {
		font-family: "Poppins", sans-serif;
		display: block;
		margin: 4rem auto 0;
		padding: 1rem 5rem;
		font-size: 2rem;
		color: var(--color-text);
		font-weight: 700;
		text-transform: capitalize;
		border: 2px solid var(--color-sandy-brown);
		border-radius: 15px;
		background: none;
		cursor: pointer;
		transition: 0.3s all ease;
		box-shadow: 0 0 5px var(--box-shadow);
	}

	.btn:hover {
		background-color: var(--color-burnt-sienna);
		font-weight: 900;
		border-color: var(--color-burnt-sienna);
		box-shadow: 0 0 15px 2px hsl(0, 0%, 20%, 0.2);
	}
</style>

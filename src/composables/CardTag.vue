<script setup></script>

<template>
	<div class="card">
		<h2>
			<slot></slot>
		</h2>
	</div>
</template>

<style scoped>
	.card {
		flex: 1;
		padding: 1rem 2rem;
		border: 1px solid var(--color-sandy-brown);
		position: relative;
		cursor: pointer;
	}

	.card:first-child {
		border-radius: 20px 0 0 0;
	}

	.signin-active:first-child::before {
		content: "";
		position: absolute;
		top: 0;
		right: 0;
		width: 2px;
		height: 100%;
		box-shadow: 5px 0 5px hsl(0, 0%, 0%, 0.4);
	}

	.signin-inactive:first-child::after {
		content: "";
		position: absolute;
		bottom: 0;
		right: 0;
		width: 100%;
		height: 2px;
		box-shadow: 0 -1px 2px hsl(0, 0%, 0%, 0.2);
	}

	.card:last-child {
		border-radius: 0 20px 0 0;
	}

	.login-active > h2,
	.signup-active > h2 {
		font-size: 2.1rem;
		transition: all 0.2s ease;
	}

	.signup-active:last-child::before {
		content: "";
		position: absolute;
		top: 0;
		left: 0;
		width: 2px;
		height: 100%;
		box-shadow: -5px 0 5px hsl(0, 0%, 0%, 0.4);
	}

	.signup-inactive:last-child::before {
		content: "";
		position: absolute;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 1px;
		box-shadow: 0 -1px 2px hsl(0, 0%, 0%, 0.2);
	}
</style>

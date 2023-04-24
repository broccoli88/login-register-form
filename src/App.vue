<template>
	<div class="container">
		<div class="cards">
			<div class="card">
				<h2>Sign In</h2>
			</div>
			<div class="card">
				<h2>Register</h2>
			</div>
		</div>
		<form action="" class="form">
			<fieldset class="fieldset">
				<legend class="legend">Log In</legend>
				<div class="input-container">
					<label for="username">Username</label>
					<input type="text" name="username" class="input" />
				</div>
				<div class="input-container">
					<label for="username">Username</label>
					<input type="text" name="username" class="input" />
				</div>
				<div class="input-container">
					<label for="username">Username</label>
					<input type="text" name="username" class="input" />
				</div>
			</fieldset>
			<button type="submit" class="btn">log in</button>
		</form>
	</div>
</template>

<style scoped>
	.container {
		width: 100%;
		max-width: 500px;
		padding: 0 0 4rem;
		background-image: linear-gradient(
			45deg,
			var(--color-saffron),
			var(--color-sandy-brown),
			var(--color-burnt-sienna)
		);

		border-radius: 20px;
		box-shadow: 0 0 15px var(--box-shadow);
		/* overflow: hidden; */
	}

	.cards {
		display: flex;
		justify-content: space-between;
	}

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

	.card:first-child::before {
		content: "";
		position: absolute;
		top: 0;
		right: 0;
		width: 2px;
		height: 100%;
		box-shadow: 5px 0 5px hsl(0, 0%, 0%, 0.4);

		display: none;
	}

	.card:last-child {
		border-radius: 0 20px 0 0;
	}

	.card:last-child::before {
		content: "";
		position: absolute;
		top: 0;
		left: 0;
		width: 2px;
		height: 100%;
		box-shadow: -5px 0 5px hsl(0, 0%, 0%, 0.4);

		display: none;
	}

	.form {
		margin-inline: 2rem;
	}

	.fieldset {
		border-color: var(--color-sandy-brown);
		border-radius: 20px;
		padding-bottom: 4rem;
	}

	.legend {
		font-size: 4rem;
		font-weight: 700;
	}

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

	.btn {
		display: block;
		margin: 4rem auto 0;
		padding: 1rem 3rem;
		font-size: 1.8rem;
		color: var(--color-text);
		font-weight: 600;
		text-transform: uppercase;
		border: 1px solid var(--color-burnt-sienna);
		border-radius: 15px;
		background: none;
		cursor: pointer;
		transition: 0.3s all ease;
	}

	.btn:hover {
		background-color: var(--color-saffron);
	}
</style>

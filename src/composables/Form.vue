<template>
	<form action="" class="form">
		<fieldset class="fieldset">
			<legend class="legend">
				<slot name="legend"></slot>
			</legend>
			<slot name="signIn"></slot>
			<slot name="signUp"></slot>
		</fieldset>
	</form>
</template>
<style scoped>
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
</style>

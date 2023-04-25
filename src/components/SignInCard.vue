<script setup>
	import Button from "../composables/Button.vue";
	import { ref } from "vue";
	import { useVuelidate } from "@vuelidate/core";
	import {
		required,
		email,
		minLength,
		maxLength,
		sameAs,
	} from "@vuelidate/validators";

	const { cardStatus } = defineProps(["card-status"]);

	// Vuelidate

	const state = ref({
		username: "",
		password: "",
	});

	const rules = {
		username: {
			required,
			minLength: minLength(3),
			maxLength: maxLength(20),
		},
		password: {
			required,
			minLength: minLength(6),
			maxLength: maxLength(20),
		},
	};

	const v = useVuelidate(rules, state);

	const submitForm = async () => {
		const isFormCorrect = await v.value.$validate();
	};
</script>
<template>
	<form action="" class="form" @submit.prevent="submitForm">
		<fieldset class="fieldset">
			<legend class="legend">Sign In</legend>

			<div class="input-container">
				<label for="username">Username</label>
				<input
					type="text"
					name="username"
					class="input"
					placeholder="Username..."
					v-model="v.username.$model"
					@blur="v.password.$touch()"
				/>
				<p v-if="v.username.$error" class="error">
					{{ v.username.$errors[0].$message }}
				</p>
			</div>
			<div class="input-container">
				<label for="password">Password</label>
				<input
					type="password"
					name="password"
					class="input"
					placeholder="Password"
					v-model="v.password.$model"
					@blur="v.password.$touch()"
				/>
				<p class="error" v-if="v.password.$error">
					{{ v.password.$errors[0].$message }}
				</p>
			</div>
		</fieldset>
		<Button>
			{{ cardStatus ? "Sign In" : "Sign Up" }}
		</Button>
	</form>
</template>

<style>
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
	.error {
		font-size: 1.1rem;
		color: crimson;
		margin-top: 0.5rem;
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

	.input::placeholder {
		opacity: 0.5;
	}
</style>

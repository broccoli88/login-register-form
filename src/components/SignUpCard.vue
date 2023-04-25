<script setup>
	import Button from "../composables/Button.vue";
	import { useVuelidate } from "@vuelidate/core";
	import {
		required,
		email,
		minLength,
		maxLength,
		sameAs,
	} from "@vuelidate/validators";
	import { ref } from "vue";

	const { cardStatus } = defineProps(["card-status"]);

	const state = ref({
		username: "",
		email: "",
		password: {
			password: "",
			repeatedPassword: "",
		},
	});

	const rules = {
		username: {
			required,
			minLength: minLength(3),
			maxLength: maxLength(20),
		},
		email: { required, email },
		password: {
			password: {
				required,
				minLength: minLength(6),
				maxLength: maxLength(20),
			},
			repeatedPassword: {
				required,
				sameAs: sameAs(state.value.password.password),
			},
		},
	};

	const v = useVuelidate(rules, state);
	const submitForm = async () => {
		const isFormCorrect = await v.value.$validate();

		if (!isFormCorrect) return;
		console.log(v.value.$errors);
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
				/>
				<p class="error" v-if="v.username.$error">
					{{ v.username.$errors[0].$message }}
				</p>
			</div>
			<div class="input-container">
				<label for="email">Email</label>
				<input
					type="text"
					name="email"
					class="input"
					placeholder="Email"
					v-model="v.email.$model"
				/>
				<p class="error" v-if="v.email.$error">
					{{ v.email.$errors[0].$message }}
				</p>
			</div>
			<div class="input-container">
				<label for="password">Password</label>
				<input
					type="password"
					name="password"
					class="input"
					placeholder="Password"
					v-model="v.password.password.$model"
				/>
				<p class="error" v-if="v.password.password.$error">
					{{ v.password.password.$errors[0].$message }}r
				</p>
			</div>
			<div class="input-container">
				<label for="repeat password">Repeat Password</label>
				<input
					type="password"
					name="repeat password"
					class="input"
					placeholder="Repeat Password"
					v-model="v.password.repeatedPassword.$model"
				/>
				<p class="error" v-if="v.password.repeatedPassword.$error">
					{{ v.password.repeatedPassword.$errors[0].$message }}
				</p>
			</div>
		</fieldset>
		<Button>
			{{ cardStatus ? "Sign In" : "Sign Up" }}
		</Button>
	</form>
</template>

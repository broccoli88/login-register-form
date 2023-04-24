<script setup>
	import Form from "./composables/Form.vue";
	import CardTag from "./composables/CardTag.vue";
	import Input from "./composables/Input.vue";
	import Button from "./composables/Button.vue";
	import SignInCard from "./components/SignInCard.vue";
	import SignUpCard from "./components/SignUpCard.vue";
	import { ref } from "vue";

	const cardStatus = ref(true);
	const logInActive = () => (cardStatus.value = true);
	const signUpActive = () => (cardStatus.value = false);
</script>

<template>
	<div class="container">
		<div class="cards">
			<CardTag
				:class="{
					'signin-active': cardStatus,
					'signin-inactive': !cardStatus,
				}"
				@click="logInActive"
			>
				Sign In
			</CardTag>
			<CardTag
				:class="{
					'signup-active': !cardStatus,
					'signup-inactive': cardStatus,
				}"
				@click="signUpActive"
				>Sign Up
			</CardTag>
		</div>

		<!-- Method I -->
		<transition name="switch" mode="out-in">
			<component :is="cardStatus ? SignInCard : SignUpCard" />
		</transition>

		<!-- Method II -->

		<!-- 
		<SignInCard v-if="cardStatus" />
		<SignUpCard v-else /> -->

		<!-- Method III -->

		<!-- <Form>
			<template v-slot:legend>
				{{ cardStatus ? "Sign In" : "Sign Up" }}
			</template>
			<template v-slot:signIn v-if="cardStatus">
				<Input> Username </Input>
				<Input> Password </Input>
			</template>
			<template v-slot:signUp v-else>
				<Input> Username </Input>
				<Input> Email </Input>
				<Input> Password </Input>
				<Input> Repeat Password </Input>
			</template>
		</Form> -->

		<Button>
			{{ cardStatus ? "Sign In" : "Sign Up" }}
		</Button>
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
		overflow: hidden;
	}

	.cards {
		display: flex;
		justify-content: space-between;
	}

	.switch-enter-from {
		opacity: 0;
		transform: translateX(150px);
	}
	.switch-leave-to {
		opacity: 0;
		transform: translateX(-150px);
	}

	.switch-enter-active,
	.switch-leave-active {
		transition: 0.4s all ease;
	}
</style>

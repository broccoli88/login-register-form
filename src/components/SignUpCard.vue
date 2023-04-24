<script setup>
	import Form from "../composables/Form.vue";
	import Input from "../composables/Input.vue";
</script>
<template>
	<Form>
		<template v-slot:legend> Sign Up </template>
		<template v-slot:signUp>
			<Input> Username </Input>
			<Input> Email </Input>
			<Input> Password </Input>
			<Input> Repeat Password </Input>
		</template>
	</Form>
</template>

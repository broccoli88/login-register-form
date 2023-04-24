<script setup>
	import Form from "../composables/Form.vue";
	import Input from "../composables/Input.vue";
</script>
<template>
	<Form>
		<template v-slot:legend> Sign In </template>
		<template v-slot:signIn>
			<Input> Username </Input>
			<Input> Password </Input>
		</template>
	</Form>
</template>

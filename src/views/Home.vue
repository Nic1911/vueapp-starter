<template>
	<div class="home">
		<img alt="Vue logo" src="../assets/logo.png" />
		<HelloWorld :msg="title" :desc="description" />
	</div>
</template>

<script>
// components
import HelloWorld from "@/components/HelloWorld.vue";
// data
import appConfig from "@/app.config.json";

export default {
	name: "Home",
	components: {
		HelloWorld,
	},
	data() {
		return {
			title: appConfig.title,
			description: appConfig.description,
		};
	},
};
</script>

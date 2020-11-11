<template>
	<div class="home">
		<img alt="Vue logo" src="../assets/logo.png" />
		<BaseMessage :msg="title" :desc="description" />
	</div>
</template>

<script>
// components
import BaseMessage from "@/components/BaseMessage.vue";
// data
import appConfig from "@/app.config.json";

export default {
	name: "Home",
	components: {
		BaseMessage,
	},
	data() {
		return {
			title: appConfig.title,
			description: appConfig.description,
		};
	},
};
</script>

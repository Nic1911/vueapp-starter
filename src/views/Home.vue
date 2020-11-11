<template>
	<Layout>
		<div class="home">
			<BaseMessage
				:class="$style.basemessage"
				:msg="title"
				:desc="description"
			/>
		</div>
	</Layout>
</template>

<script>
// components
import Layout from "@/layouts/main.vue";
import BaseMessage from "@/components/BaseMessage.vue";
// data
import appConfig from "@/app.config.json";

export default {
	name: "Home",
	components: {
		Layout,
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

<style lang="scss" module>
.basemessage {
	font-family: $system-default-font-family;
}
</style>

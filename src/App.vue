
<template>
	<div class="app">
		<h1>Hi!</h1>
		<code>{{ data ? data : "no data" }}</code>
	</div>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";

const data = ref(null);

onMounted(() => {
	fetch("./config.json")
		.then((res) => res.json())
		.then((res) => {
			data.value = res;
		})
		.catch((err) => {
			console.log("🚀 ~ file: App.vue ~ line 20 ~ .then ~ err", err);
		});
});
</script>

<style lang="scss">
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>

<template>
	<div>
		<div :style="styleObject">
			Lorem ipsum dolor sit, amet consectetur adipisicing elit. Magni provident
			excepturi dolorem dignissimos repudiandae aspernatur repellat eveniet,
			cupiditate error incidunt aliquam voluptatibus, cum libero a culpa
			accusantium neque architecto eaque.
		</div>
		<button v-on:click="fontSize--">-</button>
		<button v-on:click="fontSize++">+</button>
		<button></button>
	</div>
</template>

<script>
import { computed, ref } from 'vue';
export default {
	setup() {
		// const styleObject = reactive({
		// 	color: 'red',
		// 	fontSize: '13px',
		// });

		const fontSize = ref(13);

		const styleObject = computed(() => {
			return {
				color: 'red',
				fontSize: fontSize.value + 'px',
			};
		});
		return { styleObject, fontSize };
	},
};
</script>

<style lang="scss" scoped></style>

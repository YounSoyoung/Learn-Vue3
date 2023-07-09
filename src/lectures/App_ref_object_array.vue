<template>
	<div></div>
</template>

<script>
import { reactive, ref } from 'vue';
export default {
	setup() {
		const count = ref(0);
		const state = reactive({
			count,
		});
		count.value++;
		count.value++;
		console.log(count.value);
		console.log('state.count: ', state.count);

		// ref로 선언한 반응형 상태를 반응형 객체에 넣고 사용할 때는
		// .value를 붙이면 안된다.
		// -> state.count.value (X)

		//ref -> Array
		const message = ref('Hello');
		const arr = reactive([message]);
		console.log('state.count: ', arr[0].value);

		//반응형 상태를 배열에 넣었을 때
		//접근하기 위해서는 .value를 붙여야한다.
		//arr[0].value (O)

		return {};
	},
};
</script>

<style lang="scss" scoped></style>

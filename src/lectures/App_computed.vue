<template>
	<div>
		<h2>{{ teacher.name }}</h2>
		<h3>강의가 있습니까?</h3>
		<!-- <p>{{ teacher.lectures.length > 0 ? '있음😊' : '없음😥' }}</p> -->
		<p>{{ hasLecture }}</p>
		<p>{{ hasLecture }}</p>
		<p>{{ existLecture() }}</p>
		<p>{{ existLecture() }}</p>
		<button v-on:click="counter++">Counter : {{ counter }}</button>
		<h2>이름</h2>
		<p>{{ fullName }}</p>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		const teacher = reactive({
			name: '짐포딩',
			lectures: ['HTML/CSS', 'JavaScript', 'Vue3'],
		});

		const hasLecture = computed(() => {
			console.log('computed');
			return teacher.lectures.length > 0 ? '있음😊' : '없음😥';
		});

		const existLecture = () => {
			console.log('method');
			return teacher.lectures.length > 0 ? '있음😊' : '없음😥';
		};

		// 콘솔창을 보면
		//computed
		//method
		//method
		//위와 같은 결과가 나온다.
		// -> computed는 한 번 계산된 결과를 캐시해놓는다. 그 다음에 요청이 들어왔을 때는 저장된 결과를 돌려준다.
		//method는 실행될 때마다
		//computed가 다시 계산되는 시점은 반응형 데이터가 변경되는 시점이다.

		const counter = ref(0);

		const firstName = ref('홍');
		const lastName = ref('길동');

		const fullName = computed({
			get() {
				return firstName.value + ' ' + lastName.value;
			},
			set(value) {
				[firstName.value, lastName.value] = value.split(' ');
			},
		});
		console.log('Console 출력: ', fullName.value);
		fullName.value = '짐 코딩';

		return {
			teacher,
			hasLecture,
			existLecture,
			counter,
			fullName,
		};
	},
};
</script>

<style lang="scss" scoped></style>

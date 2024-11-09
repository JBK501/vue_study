<script setup>
import { ref, reactive, computed } from "vue";

// reactive를 사용하여 반응형 객체를 생성한다.
// author.name 이나 author.books가 변경되면, Vue가 이를 감지하고 렌더링한다.
const author = reactive({
  name: "John Doe",
  books: [
    "Vue 2 - Advanced Guide",
    "Vue 3 - Basic Guide",
    "Vue 4 - The Mystery",
  ],
});

// computed()
// - 계산된 속성 생성
// - 의존하는 객체를 대상으로 사용한다.
// - 주로 getter 용도로 사용한다.(비동기 요청, DOM 변경자제)
const publishedBooksMessage = computed(() => {
  // author.books에 의존한다.
  // author.books가 변경될 때마다 함수가 실행되어 새로운 값을 반환한다.
  return author.books.length > 0 ? "Yes" : "No";
  // 결과값은 캐시되며, author.books가 변경되지 않는 한, 재계산하지 않는다.
});

// example2
// ref()는 값을 반응형으로 만든다. (값 변경시 Vue가 감지하고 다시 랜더링함.)
const firstName = ref("Joe");
const lastName = ref("doe");

// computed를 사용하여 getter와 setter가 있는 계산된 속성을 사용한다.
const fullName = computed({
  get() {
    return firstName.value + " " + lastName.value;
  },
  set(newValue) {
    [firstName.value, lastName.value] = newValue.split(" ");
  },
});

// setter 사용 예시
(function changeFullName() {
  fullName.value = "김 철수";
})();
</script>
<template>
  <p>책 가지고 있다.</p>
  <!-- author.books 내용이 변경될 때마다, 자동으로 업데이트 된다.-->
  <span>{{ publishedBooksMessage }}</span>
  <p>풀네임 : {{ fullName }}</p>
</template>

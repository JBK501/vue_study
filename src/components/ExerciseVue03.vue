<script setup>
/* 클래스 동적 바인딩 */
import { computed, reactive, ref } from "vue";
const isActive = ref(true);
const hasError = ref(false);

// 조건부 렌더링 데이터
const awesome = ref(true);

// 리스트 렌더링 데이터
const parentMessage = ref("Parent");
const items = ref([{ message: "Foo" }, { message: "Bar" }]);

// 객체 랜더링 데이터
const myObject = reactive({
  title: "Vue에서 목록을 작성하는 방법",
  author: "홍길동",
  publishedAt: "2016-04-10",
});

// 필터링 데이터
const numbers = ref([1, 2, 3, 4, 5]);
const eventNumbers = computed(() => {
  return numbers.value.filter((n) => n % 2 === 0);
});
</script>
<template>
  <!-- 클래스 속성에 동적으로 바인딩한다.
    <div class="static active"> 로 바인딩 된다.     
  -->
  <div class="static" :class="{ active: isActive, 'text-danger': hasError }">
    체크
  </div>

  <!-- 조건부 랜더링 -->
  <button @click="awesome = !awesome">전환</button>

  <h1 v-if="awesome">Vue는 정말 멋지죠!</h1>
  <h1 v-else>아닌가요? 😂</h1>

  <!-- 리스트 랜더링 -->
  <ul>
    <!-- :key 바인딩 - 뷰 리스트 최적화를 위해 권장되는 방식-->
    <li v-for="(item, index) in items" :key="index">
      {{ parentMessage }} - {{ index }} - {{ item.message }}
    </li>
  </ul>

  <!-- 객체 리스트 랜더링-->
  <ul>
    <li v-for="(value, key, index) in myObject" :key="index">
      {{ index }}, {{ key }} : {{ value }}
    </li>
  </ul>

  <!-- 숫자 범위 리스트 랜더링-->
  <div>
    <p>숫자 리스트 랜더링</p>
    <span v-for="(n, index) in 10" :key="index">{{ n }}</span>
  </div>

  <!-- 필터링 결과 리스트 랜더링-->
  <div>
    <p>필터링 리스트 랜더링</p>
    <ul>
      <li v-for="(n, index) in eventNumbers" :key="index">{{ n }}</li>
    </ul>
  </div>
</template>

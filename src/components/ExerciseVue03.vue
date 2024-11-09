<script setup>
import { ref } from "vue";
const isActive = ref(true);
const hasError = ref(false);
</script>
<template>
  <!-- 클래스 속성에 동적으로 바인딩한다.
    <div class="static active"> 로 바인딩 된다.     
  -->
  <div class="static" :class="{ active: isActive, 'text-danger': hasError }">
    체크
  </div>
</template>

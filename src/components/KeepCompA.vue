<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
};
</script>

<template>
  <p>현재 컴포넌트: A</p>
  <span>카운트 : {{ count }}</span>
  <button @click="count++">+</button>
</template>

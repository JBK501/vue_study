<script>
export default {
  data() {
    return {
      msg: "",
    };
  },
};
</script>

<template>
  <p>현재 컴포넌트 : B</p>
  <span>메시지 : {{ msg }}</span>
  <input v-model="msg" />
</template>

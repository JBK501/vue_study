<template>
  <!-- <span>부모 컴포넌트에서온 메시지 : {{ myMessage }}</span> -->

  <!-- todo 객체 전송-->
  <div>
    <p>Text : {{ text }}</p>
    <p>Is Complete : {{ isComplete }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    // myMessage: String,

    // todo 객체 데이터
    text: {
      type: String,
      required: true,
    },
    isComplete: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

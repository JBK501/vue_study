<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<script>
export default {
  // data()에서 반환된 속성들은 반응적인 상태가 되어
  // `this` 에 노출된다.
  data() {
    return {
      count: 0,
    };
  },

  // methods는 속성 값을 변경하고 업데이트 할 수 있는 함수.
  // 템플릿 내에서 이벤트 핸들러로 바인딩 될 수 있다.
  method: {
    imcrement() {
      this.count++;
    },
  },

  // Lifecycle hook는 컴포넌트 생명주기의
  // 여러 단계에서 호출된다.
  // 이 함수는 컴포넌트가 마운트 된 후 호출된다.
  mounted() {
    console.log(`숫자 세기의 초기값은 ${this.count}`);
  },
};
</script>

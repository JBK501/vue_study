<script>
export default {
  // 부모 컴포넌트로부터 'show' 라는 prop를 받는다.
  props: {
    show: Boolean, // 모달이 보일지 여부를 결정하는 불리언 값
  },
};
</script>

<!-- 
slot - 부모컨테이너에서 해당위치에 콘텐츠를 삽입할 수 있다.
<template #header>
    <h3>custom header</h3>
</template>
부모 컨테이너에서 설정한 값으로 변경됨.
<slot name="header"> default header</slot>


$emit - 사용자 정의 이벤트를 발생시킨다. 
1. @close="showModal = false" 로 설정함. 
2. 따라서 부모 컨테이너에서 :show=showModal 설정을 통해, MyModal의 show 가 false로 변경됨.
3. v-if="show" 부분에 의해, 모달이 사라짐.
-->

<template>
  <!-- 모달에 트랜지션 효과를 적용한다. -->
  <Transition name="modal">
    <!-- show 가 true일때만 모달이 나타난다. -->
    <div v-if="show" class="modal-mask">
      <!-- 모달 내용이 들어가는 컨테이너 -->
      <div class="modal-container">
        <div class="modal-header">
          <slot name="header"> default header</slot>
        </div>
        <div class="modal-body">
          <slot name="body"> default body </slot>
        </div>
        <div class="modal-footer">
          <!-- 버튼 클릭 시, close 이벤트를 발생시켜 모달을 닫는다. -->
          <slot name="footer">
            default footer
            <button class="modal-default-button" @click="$emit('close')">
              OK
            </button>
          </slot>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: opacity 0.3s ease;
}

.modal-container {
  width: 300px;
  margin: auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
}

.modal-header h3 {
  margin-top: 0;
  color: #42b983;
}

.modal-body {
  margin: 20px 0;
}

.modal-default-button {
  float: right; /* 버튼을 오른쪽으로 정렬 */
}

/* 모달이 나타날 때, 시작상태는 투명함. */
.modal-enter-from {
  opacity: 0;
}

/* 모달이 사라질 때, 최종 상태는 투명함. */
.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>

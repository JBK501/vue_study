<script>
import MyModal from "./MyModal.vue";

export default {
  components: {
    MyModal,
  },
  data() {
    return {
      showModal: false, // 모달 표시 여부를 관리하는 데이터
    };
  },
};
</script>
<template>
  <button id="show-modal" @click="showModal = true">모달창 열기</button>
  <!-- to="body" : body 태그에 추가한다. -->
  <Teleport to="body">
    <my-modal :show="showModal" @close="showModal = false">
      <template #header>
        <h3>custom header</h3>
      </template>
    </my-modal>
  </Teleport>
</template>

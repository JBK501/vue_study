<script>
import KeepCompA from "./KeepCompA.vue";
import KeepCompB from "./KeepCompB.vue";

export default {
  components: { KeepCompA, KeepCompB },
  data() {
    return {
      current: "KeepCompA",
    };
  },
};
</script>

<template>
  <div class="demo">
    <label><input type="radio" v-model="current" value="KeepCompA" />A</label>
    <label><input type="radio" v-model="current" value="KeepCompB" />B</label>
    <KeepAlive>
      <component :is="current"></component>
    </KeepAlive>
  </div>
</template>

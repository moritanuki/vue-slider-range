<template class="wrapper">
  <VueformSlider />
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import VueformSlider from './VueformSlider.vue';

export default defineComponent({
  components: {
    VueformSlider,
  },
});
</script>
<style>
.title {
  text-align: center;
  margin: 40px;
}

.slider {
  width: 500px;
  margin: 40px;
}
</style>

<template class="wrapper">
  <div class="slider">
    <p class="title">ぬるぬる動く自作step</p>
    <Slider v-model="value" :min="0" :max="100" :lazy="false" @change="changeVolume()" />
  </div>
  <div class="slider">
    <p class="title">カクカク動くライブラリのstep</p>
    <Slider v-model="stepValue" :min="0" :max="100" :lazy="false" :step="50" />
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import Slider from '@vueform/slider';

export default defineComponent({
  components: {
    Slider,
  },
  data() {
    return {
      value: 0,
      stepValue: 0,
    };
  },
  methods: {
    changeVolume() {
      // 50ずつのステップ
      this.value = Math.round(this.value / 50) * 50;
    },
  },
});
</script>
<style src="@vueform/slider/themes/default.css"></style>
<style scoped>
.title {
  text-align: center;
  margin: 40px;
}

.slider {
  width: 500px;
  margin: 40px;
}
</style>

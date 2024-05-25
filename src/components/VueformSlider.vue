<template class="wrapper">
  <div class="slider">
    <p class="title">ぬるぬる動く自作step</p>
    <!-- NOTE: 本来のinput要素であれば、step値にanyを割り当てられる（小数点何桁でも受け入れ可能）が、
    vueform/sliderは数値のみ受け付けているためTypeScriptで弾かれてしまう。-1で同様の効果が狙える。 -->
    <Slider v-model="value" :min="0" :max="100" :lazy="false" :step="-1" :format="changeVolume"
      @change="changeVolume()" />
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

      // NOTE: tooltipに表示させる値
      // tooltipの表記はvalue値に依存するため、
      // changeイベントでvalue値を書き換えるタイミングで同期するようにしている
      return this.value
    },
  },
});
</script>
<style src="@vueform/slider/themes/default.css"></style>

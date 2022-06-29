<script setup>
import { computed, ref } from 'vue';
import cssButtons from './css/buttons-radio.module.css';
import CommonButtonsRadio from './components/CommonButtonsRadio';

const refButtonIndex = ref(0);
const getButtonIndex = computed(() => refButtonIndex.value);
const setButtonIndex = (index) => {
  refButtonIndex.value = index;
};

const propsButtons = computed(() => ({
  buttons: ['Value 1', 'Value 2'],
  indexSelected: getButtonIndex.value,
  classes: cssButtons,
}));
</script>

<template>
  <div :class="$style.outer">
    <CommonButtonsRadio
      v-bind="propsButtons"
      @select-button-index="setButtonIndex"
    />
  </div>
</template>

<style module>
.outer {
  composes: flex from './css/flex.module.css';
  width: 100%;
  padding: 0.5em 25%;
}
</style>

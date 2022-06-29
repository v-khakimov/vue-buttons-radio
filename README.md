# Radio Buttons component

## API:
props: 
```
buttons: Array,
indexSelected: Number,
classes: {
  each: [Array || String],
  first: [Array || String],
  selected: [Array || String],
  unselected: [Array || String]
}
```
All values (except of 'each') are added to 'each' value

emit:
```
const emit = defineEmits(['selectButtonIndex']);

const clickToButton = (index) => {
  emit('selectButtonIndex', index);
};
```

## Main files
```
./components/CommonButtonsRadio.vue
./css/buttons-radio.module.css
```
(you can add object from buttons-radio.module.css directli to props.classes)

## What To Do
in parent component (i.e. App.vue)
```
<script setup>
import { computed, ref } from 'vue';
import cssButtons from './css/buttons-radio.module.css';
import CommonButtonsRadio from './components/CommonButtonsRadio.vue';

const refButtonIndex = ref(0);
const setButtonIndex = (index) => {
  refButtonIndex.value = index;
};

const propsButtons = computed(() => ({
  buttons: ['Value 1', 'Value 2'],
  indexSelected: refButtonIndex.value,
  classes: cssButtons,
}));
</script>

<template>
  <div class="outer">
    <CommonButtonsRadio v-bind="propsButtons" @select-button-index="setButtonIndex" />
  </div>
</template>
```

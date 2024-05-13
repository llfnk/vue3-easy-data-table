<template>
  <div
    class="easy-checkbox"
    @click.stop.prevent="emits('change')"
  >
    <input
      type="checkbox"
      :checked="checked"
    >
    <label for="checbox" />
    {{ disabledForCheckbox }}
  </div>
</template>

<script setup lang="ts">
import { inject } from 'vue';

const emits = defineEmits(['change']);

defineProps({
  checked: { type: Boolean, required: true },
  disabledForCheckbox: {}
});

const themeColor = inject('themeColor');
</script>

<style lang="scss" scoped>
@import '../scss/checbox.scss';

$checkbox-checked-color: v-bind(themeColor);

.easy-checkbox {
  input[type="checkbox"] {
    &:checked {
      + label:before{
        background: $checkbox-checked-color;
      }
    }
  }
}
</style>

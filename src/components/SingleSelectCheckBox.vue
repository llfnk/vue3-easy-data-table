<template>
  <div
    class="easy-checkbox"
    @click.stop.prevent="changeStatus"
  >
    <input
      type="checkbox"
      :checked="checked"
      :disabled="isDisabled"
    >
    <label for="checbox" />
  </div>
</template>

<script setup lang="ts">
import { inject,computed } from 'vue';

const emits = defineEmits(['change']);

const props = defineProps({
  checked: { type: Boolean, required: true },
  disabledForCheckbox: [],
  item:{}
});

const themeColor = inject('themeColor');

const isDisabled = computed(() =>{
 return (props.disabledForCheckbox).includes(props.item?.uuid);
})

const changeStatus = () => {
  if(!(props.disabledForCheckbox).includes(props.item?.uuid)){
    emits('change')
  }

}
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

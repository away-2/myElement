<template>
     <div class="el-input">
        <input class="el-input--inner" :value="modelValue" @input="onInput"/>
        <slot></slot>
    </div>
</template>

<script lang="ts">
export default {
    name: 'ElInput'
}
</script>

<script setup lang="ts">

defineProps<{modelValue: string}>()

const emit = defineEmits<(e: 'update:model-value', value: string) => void>()
const onInput = (e) => {
    const input = e.target as HTMLInputElement
    emit('update:model-value', input.value)
}


</script>

<style scoped lang="scss">
@import '../../styles/mixin';
@include b(input) {

  @include m(inner){
   -webkit-appearance: none;
    background-color: #fff;
    background-image: none;
    border-radius: 4px;
    border: 1px solid #dcdfe6;
    box-sizing: border-box;
    color: #606266;
    display: inline-block;
    font-size: inherit;
    height: 40px;
    line-height: 40px;
    outline: 0;
    padding: 0 15px;
    transition: border-color .2s cubic-bezier(.645,.045,.355,1);
    width: 100%;
  }
}
</style>
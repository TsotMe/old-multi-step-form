<template>
<div class="custom-toggle" :class="{'checked': modelValue}" @click="$emit('update:modelValue', !modelValue)">
    <div class="white-circle" />
</div>
</template>

<script>
export default {
    name: "CustomToggle",
    props: {
        modelValue: Boolean
    },
    emits: ['update:modelValue'],
}
</script>

<style scoped lang="scss">
@use '@/assets/css/variables' as v;

.custom-toggle {
    width: 36px;
    height: 18px;
    border-radius: 16px;
    background-color: v.$Marine-blue;
    position: relative;
    cursor: pointer;

    > .white-circle {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        background-color: #FFFFFF;
        position: absolute;
        top: 3px;
        left: 3px;
        transition: left .3s ease;
    }

    &.checked {
        > .white-circle {
            left: 21px;
        }
    }
}
</style>

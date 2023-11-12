<template>
<div class="custom-toggle">

</div>
</template>

<script>
export default {
    name: "CustomToggle"
}
</script>

<style scoped lang="scss">
@use '@/assets/css/variables' as v;

.custom-toggle {
    width: 30px;
    height: 10px;
    border-radius: 6px;
    background-color: v.$Marine-blue;
}
</style>

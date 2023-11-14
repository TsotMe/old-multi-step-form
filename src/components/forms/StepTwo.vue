<template>
<div class="step-two">
    <div class="billing-type-wrapper">
        <span :class="{active: stepTwoStore.billingType === 1}">Monthly</span>
        <CustomToggle v-model="isYearly"/>
        <span :class="{active: stepTwoStore.billingType === 2}">Yearly</span>
    </div>
</div>
</template>

<script>
import CustomToggle from "@/components/UI/CustomToggle.vue";
import {useStepTwoStore} from "@/stores/StepTwoStore";

export default {
    name: "StepTwo",
    components: {CustomToggle},
    setup() {
        const stepTwoStore = useStepTwoStore()
        return {stepTwoStore}
    },
    data() {
        return {
            isYearly: false
        }
    },
    watch: {
        isYearly(newVal) {
            this.stepTwoStore.billingType = newVal ? 2 : 1
        }
    }
}
</script>

<style scoped lang="scss">
@use '@/assets/css/variables' as v;

.step-two {
    > .billing-type-wrapper {
        display: flex;
        align-items: center;
        gap: 18px;
        justify-content: center;

        > span {
            font-size: 14px;
            color: v.$Cool-gray;
            font-weight: 600;

            &.active {
                color: v.$Marine-blue;
            }
        }
    }
}
</style>

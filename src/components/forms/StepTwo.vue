<template>
<div class="step-two">
    <CustomToggle v-model="isYearly"/>
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
.step-two {

}
</style>

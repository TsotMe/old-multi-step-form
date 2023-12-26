<template>
<div class="step-two">
    <div class="plans-cont">
        <PlanComponent
            :planImage="iconArcade"
            planTitle="Arcade"
            :planInitialPrice="9"
            :class="{active: selectedPlan === 1}"
            @setSelectedPlan="selectedPlan = 1"
        />
        <PlanComponent
            :planImage="iconAdvanced"
            planTitle="Advanced"
            :planInitialPrice="12"
            :class="{active: selectedPlan === 2}"
            @setSelectedPlan="selectedPlan = 2"
        />
        <PlanComponent
            :planImage="iconPro"
            planTitle="Pro"
            :planInitialPrice="15"
            :class="{active: selectedPlan === 3}"
            @setSelectedPlan="selectedPlan = 3"
        />
    </div>
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
import PlanComponent from "@/components/second-step/PlanComponent.vue";
import iconAdvanced from "@/assets/images/icon-advanced.svg"
import iconArcade from "@/assets/images/icon-arcade.svg"
import iconPro from "@/assets/images/icon-pro.svg"

export default {
    name: "StepTwo",
    components: {PlanComponent, CustomToggle},
    setup() {
        const stepTwoStore = useStepTwoStore()
        return {stepTwoStore}
    },
    data() {
        return {
            isYearly: false,
            iconAdvanced: iconAdvanced,
            iconArcade: iconArcade,
            iconPro: iconPro,
            selectedPlan: 1
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
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 40px;

    > .plans-cont {
        display: grid;
        align-items: center;
        justify-content: space-between;
        grid-template-columns: 1fr 1fr 1fr;
        gap: 16px;

        > .active {
            border-color: black;
        }
    }

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

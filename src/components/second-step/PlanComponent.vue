<template>
<div class="plan-component" @click="$emit('setSelectedPlan')">
    <img :src="planImage" alt="">
    <div class="plan-info-wrapper">
        <h3>{{ planTitle }}</h3>
        <span>{{ planPrice }}</span>
        <span>2 months free</span>
    </div>
</div>
</template>

<script>
import {useStepTwoStore} from "@/stores/StepTwoStore";

export default {
    name: "PlanComponent",
    props: {
        planImage: {
            type: String,
            default: ''
        },
        planTitle: {
            type: String,
            default: ''
        },
        planInitialPrice: {
            type: Number,
            default: null
        }
    },
    setup() {
        const stepTwoStore = useStepTwoStore()
        return {stepTwoStore}
    },
    computed: {
        planPrice() {
            if (this.stepTwoStore.billingType === 2) {
                return `$${this.planInitialPrice * 10}/yr`
            } else {
                return `$${this.planInitialPrice}/mo`
            }
        }
    }
}
</script>

<style scoped lang="scss">
.plan-component {
    padding: 15px;
    display: flex;
    flex-direction: column;
    gap: 40px;
    transition: .2s;
    border: 1px solid white;

    &:hover {
        border-color: black;
    }

    > img {
        width: 40px;
        height: 40px;
    }

    > .plan-info-wrapper {
        > h3 {

        }

        > span {

        }

        > span {

        }
    }
}
</style>

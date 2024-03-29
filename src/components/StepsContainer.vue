<template>
<div class="steps-container">
    <div class="step-head" :class="{'last-step': currentStep === 5}">
        <img src="../assets/images/icon-thank-you.svg" v-if="currentStep === 5" alt="">
        <h2>{{ title }}</h2>
        <p>{{ description }}</p>
    </div>
    <keep-alive>
        <Component :is="stepComponent"/>
    </keep-alive>
    <div class="next-prev-buttons" v-if="currentStep !== 5" :class="{'first-step': currentStep === 1}">
        <button class="prev" v-show="currentStep !== 1" @click="handlePrevButtonCLick(currentStep - 1)">Go back</button>
        <button class="next" @click="handleNextButtonCLick(currentStep + 1)"
                :class="{'last-step': currentStep === 4}">{{ nextButtonName }}
        </button>
    </div>
</div>
</template>

<script>
import {useStepOneStore} from "@/stores/StepOneStore";
import StepOne from "@/components/forms/StepOne.vue";
import StepTwo from "@/components/forms/StepTwo.vue";

export default {
    name: "StepsContainer",
    components: {StepTwo, StepOne},
    props: {
        title: {
            type: String,
            default: ""
        },
        description: {
            type: String,
            default: ""
        },
        currentStep: {
            type: Number,
            default: null
        }
    },
    setup() {
        const stepOneStore = useStepOneStore()
        return {stepOneStore}
    },
    computed: {
        nextButtonName() {
            return this.currentStep === 4 ? 'Confirm' : 'Next Step'
        },
        stepComponent() {
            return this.currentStep === 1 ? 'StepOne' : this.currentStep === 2 ? 'StepTwo' :
                this.currentStep === 3 ? 'StepThree' : 'StepFour'
        }
    },
    methods: {
        handlePrevButtonCLick(value) {
            if (value > 0) this.$emit('update:currentStep', value)
        },
        handleNextButtonCLick(value) {
            const {name, email, phone_number} = this.stepOneStore.data

            if (value === 2) {
                if (value < 6 && name && email && phone_number) {
                    return this.$emit('update:currentStep', value)
                }

                const errorData = {
                    name: !name ? "This field is required" : '',
                    email: !email ? "This field is required" : '',
                    phone_number: !phone_number ? "This field is required" : '',
                }
                return this.stepOneStore.updateError(errorData)
            }
        }
    }
}
</script>

<style lang="scss" scoped>
.steps-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 450px;
    height: 510px;

    .step-head {
        margin-bottom: 45px;

        &.last-step {
            height: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;

            img {
                width: 80px;
                height: 80px;
                margin-bottom: 30px;
            }

            h2 {
                margin-bottom: 15px;
            }

            p {
                text-align: center;
                line-height: 24px;
            }
        }

        h2 {
            font-family: ubuntu-medium, sans-serif;
            letter-spacing: 1px;
            font-size: 26px;
            color: #00194F;
            margin-bottom: 10px;
        }

        p {
            color: #8F9094;
        }
    }

    .next-prev-buttons {
        display: flex;
        align-items: center;
        justify-content: space-between;

        &.first-step {
            justify-content: right;
        }

        .prev {
            color: #9B9BA3;
            background-color: #FFFFFF;
            font-family: ubuntu-medium, sans-serif;
            font-size: 16px;
        }

        .next {
            background-color: #03295A;
            color: #FFFFFF;
            padding: 12px 18px;
            border-radius: 6px;
            font-family: ubuntu-medium, sans-serif;
            font-size: 16px;

            &.last-step {
                background-color: #483EFF;
            }
        }
    }
}
</style>

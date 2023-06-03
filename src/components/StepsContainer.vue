<template>
    <div class="steps-container">
        <div class="step-head">
            <h2>{{ title }}</h2>
            <p>{{ description}}</p>
        </div>
        <slot />
        <div class="next-prev-buttons" :class="{'first-step': currentStep === 1}">
            <button class="prev" v-show="currentStep !== 1" @click="updateStep(currentStep - 1)">Go back</button>
            <button class="next" @click="updateStep(currentStep + 1)"
                    :class="{'last-step': currentStep === 4}">{{ nextButtonName }}</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "StepsContainer",
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
    computed: {
        nextButtonName() {
            return this.currentStep === 4 ? 'Confirm' : 'Next Step'
        }
    },
    methods: {
        updateStep(value) {
            if (value > 1 && value < 6) this.$emit('update:currentStep', value)
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
        margin-bottom: 30px;

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

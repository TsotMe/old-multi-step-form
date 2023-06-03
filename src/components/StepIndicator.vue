<template>
    <div class="steps-indicator">
        <div class="step" v-for="step in steps" :key="step.id" :class="{'active-step': step.id === currentStep}">
            <div class="step-id">
                {{ step.id }}
            </div>
            <div class="step-info">
                <span>{{ 'STEP ' + step.id }}</span>
                <p>{{ step.title }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "StepIndicator",
    props: {
        currentStep: {
            type: Number,
            default: null
        }
    },
    data() {
        return {
            steps: [
                {id: 1, title: "YOUR INFO"},
                {id: 2, title: "SELECT PLAN"},
                {id: 3, title: "ADD-ONS"},
                {id: 4, title: "SUMMARY"}
            ]
        }
    }
}
</script>

<style lang="scss" scoped>
.steps-indicator {
    height: 100%;
    background-image: url("../assets/images/bg-sidebar-desktop.svg");
    background-repeat: no-repeat;
    object-fit: cover;
    border-radius: 12px;
    padding: 35px 30px;

    .step {
        display: flex;
        align-items: center;
        gap: 15px;
        margin-bottom: 30px;

        &.active-step {
            .step-id {
                background-color: #BEE1FD;
                color: #0E2F5C;
            }
        }

        &:last-child {
            margin-bottom: 0;
        }

        .step-id {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            border: 1px solid #FFFFFF;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #FFFFFF;
            font-family: ubuntu-medium, sans-serif;
        }

        .step-info {
            display: flex;
            flex-direction: column;
            justify-content: space-between;

            span {
                color: #A6A4FF;
                font-size: 14px;
            }

            p {
                color: #F7F8FF;
                font-family: ubuntu-medium, sans-serif;
            }
        }
    }
}
</style>

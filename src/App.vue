<template>
    <div class="website">
        <main>
            <StepIndicator :currentStep="currentStep" />
            <div class="temp-class">
                <StepsContainer :title="stepData.title" :description="stepData.description" v-model:currentStep="currentStep" />
            </div>
        </main>
    </div>
</template>

<script>
import StepIndicator from "@/components/StepIndicator.vue";
import StepsContainer from "@/components/StepsContainer.vue";

export default {
    name: 'App',
    components: {
        StepsContainer,
        StepIndicator
    },
    data() {
        return {
            currentStep: 2,
            stepsListing: [
                {title: "Personal info", description: "Please provide your name, email address, and phone number."},
                {title: "Select your plan", description: "you have the option to monthly or yearly billing."},
                {title: "Pick add-ons", description: "Add-ons help enhance your gaming experience."},
                {title: "Finishing up", description: "Double-check everything looks OK before confirming."},
                {title: "Thank you!", description:
                        "Thanks for confirming your subscription! we hope you have fun using our platform. " +
                        "if you ever need support, please feel free to email us at support@loremGaming.com"}
            ]
        }
    },
    computed: {
        stepData() {
            return this.stepsListing[this.currentStep - 1]
        }
    }
}
</script>

<style lang="scss">
.website {
    width: 100%;
    height: 100vh;
    background-color: #EEF5FF;
    display: flex;
    align-items: center;
    justify-content: center;

    main {
        background-color: #FFFFFF;
        padding: 20px;
        width: 900px;
        border-radius: 14px;
        height: 610px;
        display: grid;
        grid-template-columns: 274px auto;

        .temp-class {
            display: flex;
            align-items: center;
            justify-content: center;
        }
    }
}
</style>

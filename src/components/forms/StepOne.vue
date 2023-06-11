<template>
    <div class="step-one">
        <CustomInput
            type="text"
            labelText="Name"
            placeholderText="e.g. Stephen King"
            :errorText="stepOneStore.error.name"
            v-model="stepOneData.name"
        />
        <CustomInput
            type="email"
            labelText="Email Address"
            placeholderText="e.g. stephenking@lorem.com"
            :errorText="stepOneStore.error.email"
            v-model="stepOneData.email"
        />
        <CustomInput
            type="number"
            labelText="Phone Number"
            placeholderText="e.g. +1 234 567 890"
            :errorText="stepOneStore.error.phone_number"
            v-model="stepOneData.phone_number"
        />
    </div>
</template>

<script>
import CustomInput from "@/components/CustomInput.vue";
import { useStepOneStore } from "@/stores/StepOneStore"

export default {
    name: "StepOne",
    components: { CustomInput },
    setup() {
        const stepOneStore = useStepOneStore()
        return { stepOneStore }
    },
    data() {
        return {
            stepOneData: {
                name: '',
                email: '',
                phone_number: null
            }
        }
    },
    watch: {
        stepOneData:  {
            handler(newValue) {
                this.stepOneStore.updateData(newValue)
            },
            deep: true
        }
    }
}
</script>

<style lang="scss" scoped>
.step-one {
    height: 100%;
    display: flex;
    flex-direction: column;
    gap: 25px;
}
</style>

<template>
    <div class="website">
        <main>
            <StepIndicator/>
            <div class="temp-class">
                <StepsContainer title="title" description="bla bla bla"/>
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
    }
}
</script>

<style lang="scss" scoped>
@import './assets/css/variables.scss';

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

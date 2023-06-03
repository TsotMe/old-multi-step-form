<template>
    <div class="website">
        <main>
            <StepIndicator/>
            <!-- steps here -->
        </main>
    </div>
</template>

<script>
import StepIndicator from "@/components/StepIndicator.vue";

export default {
    name: 'App',
    components: {
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
        height: 600px;
        display: grid;
        grid-template-columns: 274px auto;
    }
}
</style>

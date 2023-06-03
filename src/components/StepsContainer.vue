<template>
    <div class="steps-container">
        <div class="step-head">
            <h2>{{ title }}</h2>
            <p>{{ description}}</p>
        </div>
        <slot />
        <div class="next-prev-buttons">
            <button class="prev">Go back</button>
            <button class="next">Next Step</button>
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
        }
    }
}
</style>

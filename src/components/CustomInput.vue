<template>
    <div class="custom-input">
        <div class="custom-input-head">
            <label>{{ labelText }}</label>
            <span>{{ errorText }}</span>
        </div>
        <input :type="type" :placeholder="placeholderText">
    </div>
</template>

<script>
export default {
    name: "CustomInput",
    props: {
        labelText: {
            type: String,
            default: ''
        },
        errorText: {
            type: String,
            default: ''
        },
        placeholderText: {
            type: String,
            default: ''
        },
        type: {
            type: String,
            default: ''
        }
    }
}
</script>

<style lang="scss" scoped>
.custom-input {
    width: 100%;
    height: fit-content;

    .custom-input-head {
        display: flex;
        align-items: center;
        justify-content: space-between;

        label {

        }

        span {

        }
    }

    input {
        width: 100%;
        height: 38px;
    }
}
</style>

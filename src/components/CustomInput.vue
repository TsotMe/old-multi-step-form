<template>
    <div class="custom-input">
        <div class="custom-input-head">
            <label>{{ labelText }}</label>
            <span>{{ errorText }}</span>
        </div>
        <input :type="type" :placeholder="placeholderText" v-model="value">
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
        },
        modelValue: {
            type: [String, Number],
            default: null
        }
    },
    emits: ['update:modelValue'],
    computed: {
        value: {
            get() {
                return this.modelValue
            },
            set(value) {
                this.$emit('update:modelValue', value)
            }
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
        margin-bottom: 8px;

        label {
            color: #00194F;
        }

        span {
            color: #D2545F;
            font-family: ubuntu-medium, sans-serif;
        }
    }

    input {
        width: 100%;
        height: 48px;
        border-radius: 6px;
        border: 1px solid #9B9BA3;
        color: #081C3D;
        padding-left: 10px;
        font-family: ubuntu-medium, sans-serif;
        font-size: 16px;
    }

    input:focus {
        border: 1px solid #554F95;
    }

    input::placeholder {
        color: #9B9BA3;
    }
}
</style>

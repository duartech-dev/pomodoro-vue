<script setup>
import { reactive, computed } from 'vue'
const props = defineProps({
    modelValue: {
        type: Object,
        required: true
    },
    prevStep: {
        type: Function,
        required: true
    },

})
const emit = defineEmits(['update:modelValue'])

const enableForm = computed(() => {
    return props.modelValue.name === '' || props.modelValue.lastName === '' || props.modelValue.email === ''
})
const handleSubmit = () => {
    emit('update:modelValue', props.modelValue)
    console.log(props.modelValue)
}
</script>

<template>
    <div>
        <form @submit.prevent="handleSubmit()">
            <label for="name">
                Name
            </label>
            <input type="text" v-model="modelValue.name" placeholder="Name" id="name" />
            <label for="lastName">
                Last Name
            </label>
            <input type="text" v-model="modelValue.lastName" placeholder="Last Name" id="lastName" />
            <label for="email">
                Email
            </label>
            <input type="email" v-model="modelValue.email" placeholder="Email" id="email" />

            <div>
                <button type="button" @click="prevStep">Back</button>
                <button :disabled="enableForm" type="submit">Submit</button>
            </div>
        </form>
    </div>
</template>

<style scoped></style>

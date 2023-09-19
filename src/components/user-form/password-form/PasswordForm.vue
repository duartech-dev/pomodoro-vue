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
const state = reactive({
    password: '',
    confirmPassword: '',

})
const enableform = computed(() => {
    return false
})
const handleSubmit = () => {
    emit('update:modelValue', state)
    console.log(state)
}
</script>

<template>
    <div>
        <form @submit.prevent="handleSubmit()">
            <label for="password">
                Password
            </label>
            <input type="password" v-model="state.password" placeholder="Password" id="password" />
            <label for="confirmPassword">
                Confirm Password
            </label>
            <input type="password" v-model="state.confirmPassword" placeholder="Confirm Password" id="confirmPassword" />
            <div>
                <button type="button" @click="prevStep">Back</button>
                <button :disabled="enableform" type="submit">Submit</button>
            </div>
        </form>
    </div>
</template>

<style scoped></style>

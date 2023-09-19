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


const enableform = computed(() => {
    return false
})
const handleSubmit = () => {
    emit('update:modelValue', props.modelValue)

}
</script>

<template>
    <div>
        <form @submit.prevent="handleSubmit()">
            <label for="address">
                Address
            </label>
            <input type="text" v-model="modelValue.address" placeholder="Address" id="address" />
            <label for="city">
                City
            </label>
            <input type="text" v-model="modelValue.city" placeholder="City" id="city" />
            <label for="state">
                State
            </label>
            <input type="text" v-model="modelValue.state" placeholder="State" id="state" />
            <label for="country">
                Country
            </label>
            <input type="text" v-model="modelValue.country" placeholder="Country" id="country" />
            <label for="zipCode">
                Zip Code
            </label>
            <input type="text" v-model="modelValue.zipCode" placeholder="Zip Code" id="zipCode" />


            <div>
                <button type="button" @click="prevStep">Back</button>
                <button :disabled="enableform" type="submit">Submit</button>
            </div>
        </form>
    </div>
</template>

<style scoped></style>

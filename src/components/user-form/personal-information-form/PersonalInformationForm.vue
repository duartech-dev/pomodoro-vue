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
const genres = ["Male", "Female", "Other"]


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
            <label for="age">
                Age
            </label>
            <input type="number" v-model="modelValue.age" placeholder="Age" id="age" />
            <label for="genre">
                Genre
            </label>
            <select v-model="modelValue.genre" placeholder="Genre" id="genre">
                <option v-for="genre in genres" :key="genre" :value="genre">{{ genre }}</option>
            </select>

            <label for="phone">
                Phone
            </label>
            <input type="text" v-model="modelValue.phone" placeholder="Phone" id="phone" />
            <label for="birthDate">
                Birth Date
            </label>
            <input type="date" v-model="modelValue.birthDate" placeholder="Birth Date" id="birthDate" />

            <div>
                <button type="button" @click="prevStep">Back</button>
                <button :disabled="enableform" type="submit">Submit</button>
            </div>
        </form>
    </div>
</template>

<style scoped></style>

<script setup>

import { ref, reactive } from 'vue'
import BasicForm from './components/user-form/basic-form/BasicForm.vue'
import PersonalForm from './components/user-form/personal-information-form/PersonalInformationForm.vue'
import AddressForm from './components/user-form/address-form/AddressForm.vue'
import PasswordForm from './components/user-form/password-form/PasswordForm.vue'

const maxStep = 4

const currentStep = ref(1)

const stateBasicForm = reactive({
  name: '',
  lastName: '',
  email: '',

})
const statePersonalForm = reactive({
  age: 0,
  genre: '',
  phone: '',
  birthDate: '',

})
const stateAddress = reactive({
  address: '',
  city: '',
  state: '',
  country: '',
  zipCode: '',

})
const statePassword = reactive({
  password: '',
  confirmPassword: '',

})

const nextStep = () => {
  if (currentStep.value < maxStep)
    currentStep.value++
}
const prevStep = () => {
  if (currentStep.value > 1)
    currentStep.value--
}
const handleBasicForm = (data) => {
  console.log({ data })
  nextStep()

}

const handlePersonalForm = (data) => {
  console.log({ data })
  nextStep()

}
const handleAddressForm = (data) => {
  console.log({ data })
  nextStep()

}
const handlePasswordForm = (data) => {
  console.log({ data })
  nextStep()

}
</script>

<template>
  <div>
    <div v-if="currentStep === 1">
      <BasicForm :modelValue="stateBasicForm" :prevStep="prevStep" @update:modelValue="handleBasicForm" />
    </div>
    <div v-if="currentStep === 2">
      <PersonalForm :modelValue="statePersonalForm" :prevStep="prevStep" @update:modelValue="handlePersonalForm" />
    </div>

    <div v-if="currentStep === 3">
      <AddressForm :modelValue="stateAddress" :prevStep="prevStep" @update:modelValue="handleAddressForm" />
    </div>
    <div v-if="currentStep === 4">
      <PasswordForm :modelValue="statePassword" :prevStep="prevStep" @update:modelValue="handlePasswordForm" />
    </div>
  </div>
</template>



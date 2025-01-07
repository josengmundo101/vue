<script setup>
import { requiredValidator, emailValidator } from '@/utils/validators'
import { ref } from 'vue'

const visible = ref(false)
const refVForm = ref()

const formDataDefault = {
  email: '',
  password: '',
}

const formData = ref({
  ...formDataDefault,
})

const onLogin = () => {
  alert(formData.value.password)
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({ valid }) => {
    if (valid) onLogin()
  })
}
</script>

<template>
  <v-form ref="refVForm" fast-fail @submit.prevent="onFormSubmit">
    <v-text-field
      v-model="formData.email"
      prepend-inner-icon="mdi-email"
      label="Email"
      :rules="[requiredValidator, emailValidator]"
    ></v-text-field>

    <v-text-field
      v-model="formData.password"
      :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
      :type="visible ? 'text' : 'password'"
      label="Password"
      prepend-inner-icon="mdi-lock-outline"
      @click:append-inner="visible = !visible"
      :rules="[requiredValidator]"
    ></v-text-field>

    <v-btn class="mt-2" type="submit" block color="primary" prepend-icon="mdi-login">Login</v-btn>
  </v-form>
</template>

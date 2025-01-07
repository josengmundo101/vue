<script setup>
import {
  confirmedValidator,
  emailValidator,
  passwordValidator,
  requiredValidator,
} from '@/utils/validators'
import { ref } from 'vue'

const isPasswordVisible = ref(false)
const isConfirmPasswordVisible = ref(false)
const refVForm = ref()

const formDataDefault = {
  firstname: '',
  lastname: '',
  email: '',
  password: '',
  confirm_password: '',
}

const formData = ref({ ...formDataDefault })

const onRegister = () => {
  // alert(formData.value.password)
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({ valid }) => {
    if (valid) onRegister()
  })
}
</script>

<template>
  <v-form ref="refVForm" @submit.prevent="onFormSubmit">
    <v-row>
      <v-col cols="12" md="6">
        <v-text-field
          label="First name"
          v-model="formData.firstname"
          prepend-inner-icon="mdi-account"
          :rules="[requiredValidator]"
        ></v-text-field>
      </v-col>

      <v-col cols="12" md="6">
        <v-text-field
          label="Last name"
          v-model="formData.lastname"
          prepend-inner-icon="mdi-account"
          :rules="[requiredValidator]"
        ></v-text-field>
      </v-col>

      <v-col cols="12">
        <v-text-field
          label="Email"
          prepend-inner-icon="mdi-email"
          :rules="[requiredValidator, emailValidator]"
          v-model="formData.email"
        ></v-text-field>
      </v-col>

      <v-col cols="12" md="6">
        <v-text-field
          :append-inner-icon="isPasswordVisible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="isPasswordVisible ? 'text' : 'password'"
          label="Password"
          prepend-inner-icon="mdi-lock-outline"
          @click:append-inner="isPasswordVisible = !isPasswordVisible"
          :rules="[requiredValidator, passwordValidator]"
          v-model="formData.password"
        ></v-text-field>
      </v-col>

      <v-col cols="12" md="6">
        <v-text-field
          :append-inner-icon="isConfirmPasswordVisible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="isConfirmPasswordVisible ? 'text' : 'password'"
          label="Confirmation Password"
          prepend-inner-icon="mdi-lock-outline"
          @click:append-inner="isConfirmPasswordVisible = !isConfirmPasswordVisible"
          :rules="[
            requiredValidator,
            confirmedValidator(formData.confirm_password, formData.password),
          ]"
          v-model="formData.confirm_password"
        ></v-text-field>
      </v-col>

      <v-btn class="mt-2" type="submit" block color="primary" prepend-icon="mdi-account-plus"
        >Register</v-btn
      >
    </v-row>
  </v-form>
</template>

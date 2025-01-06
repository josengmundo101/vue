<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
</script>
<template>
  <AppLayout>
    <template #content>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto pt-16">
          <v-card elevation="24">
            <v-card-title>
              <v-img src="/public/logo.png" width="15%" class="mx-auto"></v-img>
              <h2 class="font-weight-black text-center">Onepiece Online Shop</h2>
              <p class="text-center">Register Form</p>
            </v-card-title>

            <v-divider class="my-5"></v-divider>

            <v-card-text class="bg-surface-light pt-4">
              <v-form fast-fail @submit.prevent>
                <v-text-field label="First name" variant="outlined"></v-text-field>
                <v-text-field label="Last name" variant="outlined"></v-text-field>
                <v-text-field label="Email" variant="outlined"></v-text-field>

                <v-text-field label="Password" type="password" variant="outlined"></v-text-field>

                <v-text-field
                  label="Password Confirmation"
                  type="password"
                  variant="outlined"
                ></v-text-field>

                <v-btn
                  class="mt-2"
                  type="submit"
                  block
                  color="primary"
                  prepend-icon="mdi-account-plus"
                  >Register</v-btn
                >
              </v-form>

              <v-divider class="my-5"></v-divider>

              <h5 class="text-center">
                Already have account?
                <RouterLink to="/" class="text-primary">Click here to Login</RouterLink>
              </h5>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>

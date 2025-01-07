<script setup>
import RegisterForm from '@/components/auth/RegisterForm.vue'
import AppLayout from '@/components/layout/AppLayout.vue'
</script>
<template>
  <AppLayout>
    <template #content>
      <v-container fluid>
        <v-row>
          <v-col cols="12" md="8" class="bg-surface-light h-screen" v-if="!mobile"></v-col>
          <v-col cols="12" md="4" :class="mobile ? '' : 'pt-10'">
            <v-card elevation="24">
              <v-card-title>
                <v-img src="/public/logo.png" width="15%" class="mx-auto"></v-img>
                <h2 class="font-weight-black text-center">Onepiece Online Shop</h2>
                <p class="text-center">Register Form</p>
              </v-card-title>

              <v-divider class="my-5"></v-divider>

              <v-card-text class="bg-surface-light pt-4">
                <RegisterForm />

                <v-divider class="my-5"></v-divider>

                <h5 class="text-center">
                  Already have account?
                  <RouterLink to="/" class="text-primary font-weight-black"
                    >Click here to Login</RouterLink
                  >
                </h5>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </template>
  </AppLayout>
</template>

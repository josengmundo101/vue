<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import LoginForm from '@/components/auth/LoginForm.vue'
import { useDisplay } from 'vuetify'

const { mobile } = useDisplay()
</script>

<template>
  <AppLayout>
    <template #content>
      <v-container fluid>
        <v-row>
          <v-col cols="12" md="8" class="bg-surface-light h-screen" v-if="!mobile"></v-col>
          <v-col cols="12" md="4" :class="mobile ? '' : 'pt-16'">
            <v-card class="mx-auto" elevation="24" max-width="600">
              <v-card-title>
                <v-img
                  src="/public/logo.png"
                  :width="mobile ? '75%' : '25%'"
                  class="mx-auto"
                ></v-img>
                <h2 class="font-weight-black text-center">Onepiece Online Shop</h2>
                <p class="text-center">Welcome Onepiece</p>
              </v-card-title>

              <v-divider class="my-5"></v-divider>

              <v-card-text class="bg-surface-light pt-4">
                <LoginForm />

                <v-divider class="my-5"></v-divider>

                <h5 class="text-center">
                  Don't have account?
                  <RouterLink class="text-primary font-weight-black" to="/register"
                    >Click here to Register</RouterLink
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

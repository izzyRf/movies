<script setup lang="ts">
const pending = ref(false)

const paymentMethods = ['stripe', 'paypal', 'mercadopago']
const paymentMethod = ref('paypal')

const pay = async () => {
	pending.value = true

	const response = await $fetch<{ url: string }>('/api/create-order', {
		method: 'POST',
		body: {
			product_name: 'prueba',
			price: 50,
			payment_method: paymentMethod.value,
		},
	})

	pending.value = false

	if (response.url) {
		window.location.href = response.url
	} else {
		alert('Something went wrong')
	}
}
</script>

<template>
	<v-container class="d-flex flex-column gap-6 align-center py-24 mt-10">
  <v-card class="max-w-sm w-full">
    <template #header>
      <h1 class="font-bold text-xl text-center">Payments in Nuxt</h1>
    </template>
    <v-select
      v-model="paymentMethod"
      :items="['stripe', 'paypal', 'mercadopago']"
      class="mb-4"
    ></v-select>
    <v-btn
      @click="pay"
      :loading="pending"
      block
      large
      icon="mdi-credit-card"
    >
      Pay Now
    </v-btn>
  </v-card>
</v-container>
</template>
<script setup>
import { ref, inject } from 'vue'
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'
import InfoBlock from './InfoBlock.vue'
import axios from 'axios'

const props = defineProps({
  totalPrice: Number
})

const { cart, closeDrawer } = inject('cart')

const isCreatingOrder = ref(false)
const orderId = ref(null)

const createOrder = async () => {
  try {
    isCreatingOrder.value = true
    const { data } = await axios.post(`https://79da9b92723d58b9.mokky.dev/order`, {
      items: cart.value,
      totalPrice: props.totalPrice.value
    })

    cart.value = []

    orderId.value = data.id
  } catch (error) {
    console.error(error)
  } finally {
    isCreatingOrder.value = false
  }
}
</script>

<template>
  <div class="fixed left-0 top-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHead />

    <div v-if="!totalPrice || orderId" class="flex h-full items-center">
      <InfoBlock
        v-if="!totalPrice && !orderId"
        title="The cart is empty"
        image-url="/package-icon.png"
        desc="Please, add one or more sneakers to make an order"
      />
      <InfoBlock
        v-if="orderId"
        title="Your order has been placed"
        image-url="/order-success-icon.png"
        :desc="`Your order #000${orderId} will be transferred to the delivery service soon`"
      />
    </div>

    <CartItemList />

    <div v-if="totalPrice" class="flex flex-col gap-4 mt-7">
      <div class="flex gap-2">
        <span>Total:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>{{ totalPrice }} $</b>
      </div>

      <div class="flex gap-2">
        <span>Tax 8%:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b> {{ ((totalPrice / 100) * 8).toFixed(2) }} $</b>
      </div>
      <button
        :disabled="!totalPrice || isCreatingOrder"
        @click="createOrder"
        class="mt-4 bg-lime-500 w-full rounded-xl py-3 text-white disabled:bg-slate-400 hover:bg-lime-600 active:bg-lime-700 transition cursor-pointer"
      >
        Checkout
      </button>
    </div>
  </div>
</template>

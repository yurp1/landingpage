<template>
    <div class="q-pa-md">
      <q-list>
        <q-item v-for="item in cart" :key="item.id">
          <q-item-section avatar>
            <q-img :src="item.image" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ item.name }}</q-item-label>
            <q-item-label caption>Rp{{ item.price }}</q-item-label>
          </q-item-section>
          <q-item-section side>
            <q-btn icon="delete" color="negative" @click="removeFromCart(item.id)" />
          </q-item-section>
        </q-item>
      </q-list>
      <q-btn label="Checkout" color="primary" class="q-mt-md" @click="checkout" />
      <q-btn label="Back to Shop" color="secondary" class="q-mt-md" @click="$emit('navigate', 'shop')" />
    </div>
  </template>
  
  <script>
  export default {
    name: 'CartPage',
    data() {
      return {
        cart: [
          { id: 1, name: 'PAJERO', price: 439, image: 'https://i.pinimg.com/736x/dd/8a/84/dd8a845fafc4fec440730db9adfe71e9.jpg' },
          { id: 2, name: 'AYLA', price: 200, image: 'https://i.pinimg.com/564x/4a/e4/f6/4ae4f6398f669c5b42d7e6e3ad15cd30.jpg' },
          { id: 3, name: 'TRITON 2021', price: 489, image: 'https://i.pinimg.com/564x/60/d7/a6/60d7a65f9c7b4bb19eea787ccd996563.jpg' }, // Produk baru
          { id: 4, name: 'Innova Reborn V Diesel Automatic 2020 Putih', price: 419, image: 'https://i.pinimg.com/564x/d4/c6/e4/d4c6e4c2907f685b4538516fac68859b.jpg' }  // Produk baru
        ]
      }
    },
    methods: {
      removeFromCart(id) {
        this.cart = this.cart.filter(item => item.id !== id);
      },
      checkout() {
        // Logic for checkout
        this.$q.notify({ message: 'Proceed to checkout', color: 'blue', position: 'top' });
      }
    }
  }
  </script>
  
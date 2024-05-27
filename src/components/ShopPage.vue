<template>
    <div class="q-pa-md">
      <div class="q-gutter-md">
        <q-card v-for="product in products" :key="product.id" class="my-card">
          <q-img :src="product.image" class="my-card-img" />
          <q-card-section>
            <div class="text-h6">{{ product.name }}</div>
            <div class="text-subtitle1">Rp{{ product.price }}</div>
            <q-btn label="View Details" color="primary" @click="$emit('navigate', 'product', product.id)" />
          </q-card-section>
        </q-card>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ShopPage',
    data() {
      return {
        products: [
          { id: 1, name: 'PAJERO', price: 439, image: 'https://i.pinimg.com/736x/dd/8a/84/dd8a845fafc4fec440730db9adfe71e9.jpg' },
          { id: 2, name: 'AYLA', price: 200, image: 'https://i.pinimg.com/564x/4a/e4/f6/4ae4f6398f669c5b42d7e6e3ad15cd30.jpg' },
          { id: 3, name: 'TRITON 2021', price: 489, image: 'https://i.pinimg.com/564x/60/d7/a6/60d7a65f9c7b4bb19eea787ccd996563.jpg' }, // Produk baru
          { id: 4, name: 'Innova Reborn V Diesel Automatic 2020 Putih', price: 419, image: 'https://i.pinimg.com/564x/d4/c6/e4/d4c6e4c2907f685b4538516fac68859b.jpg' }  // Produk baru
        ]
      }
    }
  }
  </script>
  
  <style scoped>
  .my-card {
    width: 200px;
    margin: 10px;
  }
  .my-card-img {
    height: 150px;
  }
  </style>
  
<template>
  <div class="q-pa-md">
    <q-card>
      <q-img :src="product.image" class="my-card-img" />
      <q-card-section>
        <div class="text-h6">{{ product.name }}</div>
        <div class="text-subtitle1">Rp{{ product.price }}</div>
        <div>{{ product.description }}</div>
        <q-btn label="Add to Cart" color="primary" @click="addToCart" />
        <q-btn label="Back to Shop" color="secondary" @click="$emit('navigate', 'shop')" />
      </q-card-section>
    </q-card>
  </div>
</template>

<script>
export default {
  name: 'ProductDetailPage',
  props: ['productId'],
  data() {
    return {
      products: [
        { id: 1, name: 'PAJERO', price: 439, description: 'ISENG - ISENG', image: 'https://i.pinimg.com/736x/dd/8a/84/dd8a845fafc4fec440730db9adfe71e9.jpg' },
        { id: 2, name: 'AYLA', price: 200, description: 'ISENG - ISENG', image: 'https://i.pinimg.com/736x/dd/8a/84/dd8a845fafc4fec440730db9adfe71e9.jpg' },
        { id: 3, name: 'TRITON 2021', price: 489, description: 'ISENG - ISENG', image: 'https://i.pinimg.com/736x/dd/8a/84/dd8a845fafc4fec440730db9adfe71e9.jpg' },
        { id: 4, name: 'Innova Reborn V Diesel Automatic 2020 Putih', price: 419, description: 'ISENG - ISENG', image: 'https://i.pinimg.com/736x/dd/8a/84/dd8a845fafc4fec440730db9adfe71e9.jpg' }
      ],
      product: {}
    }
  },
  mounted() {
    // Cari produk berdasarkan productId
    this.product = this.products.find(p => p.id == this.productId);
  },
  methods: {
    addToCart() {
      // Logic untuk menambahkan ke keranjang belanja
      this.$q.notify({ message: 'Added to cart', color: 'green', position: 'top' });
    }
  }
}
</script>

<style scoped>
.my-card-img {
  height: 300px;
}
</style>

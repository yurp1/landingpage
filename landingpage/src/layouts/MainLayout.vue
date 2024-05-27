<template>
  <q-layout view="hHh lpR fFf">
    <!-- Header with Navbar -->
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-toolbar-title>
          <img src="https://cdn.quasar.dev/logo-v2/svg/logo.svg" alt="My Marketplace" height="42px" class="q-mr-sm" />
          Liat Mobil
        </q-toolbar-title>
        <q-space />
        <q-btn flat label="Shop" class="text-white" @click="navigateTo('shop')" />
        <q-btn flat label="Cart" class="text-white" @click="navigateTo('cart')" />
      </q-toolbar>
    </q-header>

    <!-- Main Page Container -->
    <q-page-container>
      <component :is="currentPage" :product-id="currentProductId" @navigate="navigate" />
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-primary text-white">
      <q-toolbar class="justify-center">
        <q-toolbar-title class="text-center text-white">
          Beli Disini Aja
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import ShopPage from '../components/ShopPage.vue'
import ProductDetailPage from '../components/ProductDetailPage.vue'
import CartPage from '../components/CartPage.vue'

export default {
  name: 'MainLayout',
  components: {
    ShopPage,
    ProductDetailPage,
    CartPage
  },
  data() {
    return {
      currentPage: 'ShopPage',
      currentProductId: null
    }
  },
  methods: {
    navigate(page, productId = null) {
      this.currentPage = this.pageComponent(page);
      this.currentProductId = productId;
    },
    navigateTo(page) {
      this.currentPage = this.pageComponent(page);
      this.currentProductId = null;
    },
    pageComponent(page) {
      switch(page) {
        case 'shop':
          return 'ShopPage';
        case 'product':
          return 'ProductDetailPage';
        case 'cart':
          return 'CartPage';
        default:
          return 'ShopPage';
      }
    }
  }
}
</script>

<style scoped>
.justify-center {
  justify-content: center;
}
.text-center {
  text-align: center;
}
</style>

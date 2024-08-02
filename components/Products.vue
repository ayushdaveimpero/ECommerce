<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const products = ref([])
const loading = ref(false)
const error = ref(null)

const fetchProducts = async () => {
  loading.value = true
  error.value = null
  try {
    const response = await axios.get('https://fakestoreapi.com/products')
    products.value = response.data
  } catch (err) {
    error.value = 'Failed to fetch products'
  } finally {
    loading.value = false
  }
}

onMounted(fetchProducts)
</script>
<template>
  <div class="container my-4">
    <h1 class="mb-4">Products</h1>
    <div class="row">
      <div v-if="loading" class="col-md-3 mb-4" v-for="n in 20" :key="n">
        <div class="card">
          <div class="card-img-top bg-light p-5"></div>
          <div class="card-body">
            <div class="bg-light mb-2 rounded" style="height: 20px; width: 60%;"></div>
            <div class="bg-light mb-2 rounded" style="height: 14px; width: 80%;"></div>
            <div class="bg-light rounded" style="height: 14px; width: 80%;"></div>
          </div>
        </div>
      </div>

      <div v-if="error" class="alert alert-danger col-12">{{ error }}</div>

      <div v-if="!loading && !error" class="col-md-3 mb-4" v-for="product in products" :key="product.id">
        <div class="card p-1">
          <img :src="product.image" class="card-img-top" height="250" width="250" alt="Product Image">
          <div class="card-body">
            <h5 class="card-title text-truncate">{{ product.title }}</h5>
            <p class="card-text text-truncate">{{ product.description }}</p>
            <p class="card-text"><strong>${{ product.price }}</strong></p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


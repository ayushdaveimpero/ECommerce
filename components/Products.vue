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
      <div v-if="!loading" class="col-md-3 mb-4" v-for="n in 20" :key="n">
        <div class="card" aria-hidden="true">
          <div class="card-img-top bg-light p-5"></div>
          <div class="card-body">
            <h5 class="card-title placeholder-glow">
              <span class="placeholder col-6"></span>
            </h5>
            <p class="card-text placeholder-glow">
              <span class="placeholder col-7"></span>
              <span class="placeholder col-4"></span>
              <span class="placeholder col-4"></span>
              <span class="placeholder col-6"></span>
              <span class="placeholder col-8"></span>
            </p>
            <div class="d-flex flex-column gap-2">
            <a href="#" tabindex="-1" class="btn btn-primary disabled placeholder col-12"></a>
            <a href="#" tabindex="-1" class="btn btn-warning disabled placeholder col-12"></a>
          </div>
          </div>
        </div>
      </div>

      <div v-if="error" class="alert alert-danger col-12">{{ error }}</div>

      <div v-if="loading && !error" class="col-md-3 mb-4" v-for="product in products" :key="product.id">
        <div class="card p-1">
          <img :src="product.image" class="card-img-top" height="250" width="250" alt="Product Image">
          <div class="card-body">
            <h5 class="card-title text-truncate">{{ product.title }}</h5>
            <p class="card-text text-truncate">{{ product.description }}</p>
            <p class="card-text"><strong>${{ product.price }}</strong></p>
            <div class="d-flex flex-column gap-2">
              <button class="btn btn-primary">Add to cart</button>
              <button class="btn btn-warning">Buy now</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
/* No additional styles needed if you're using Bootstrap's placeholder-glow */
</style>

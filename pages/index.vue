<template>
    <div class="container">
      <h3>Menu</h3>
      <div class="row">
        <div class="col-md-4" v-for="product in products" :key="product.id">
          <NuxtLink :to="'/products/' + product.id" class="card-link">
            <div class="card mb-3">
              <img :src="product.img" class="card-img-top" alt="Product Image">
              <div class="card-body">
                <h5 class="card-title">{{ product.name }}</h5>
                <p class="card-text">{{ product.description }}</p>
                <p class="card-text">Price: ${{ product.price }}</p>
                <p class="card-text">Size: {{ product.size }}</p>
                <p class="card-text">Weight: {{ product.weight }}</p>
              </div>
            </div>
          </NuxtLink>
        </div>
      </div>
    </div>
  </template>
  
  
  <script setup>
    import { ref, onMounted } from 'vue';
  
    const products = ref([]);

  
    onMounted(async () => {
      try {
        const response = await fetch('http://localhost:8000/api/products');
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await response.json();
        products.value = data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    });
  </script>
  
  <style scope>
    img {
        height:300px;
        object-fit: cover;
    }

    .card-link {
        text-decoration: none; /* Remove underline from link */
        color: inherit; /* Inherit text color */
    }

    .card-link:hover {
        text-decoration: none; /* Remove underline on hover */
        color: inherit; /* Inherit text color on hover */
    }
  </style>
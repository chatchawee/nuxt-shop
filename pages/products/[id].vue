<template>
    <div>
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-md-8">
            <div class="card mb-3">
              <div class="row g-0">
                <div class="col-md-6">
                  <img :src="product.img" class="img-fluid rounded-start" alt="Product Image">
                </div>
                <div class="col-md-6">
                  <div class="card-body">
                    <h5 class="card-title">{{ product.name }}</h5>
                    <p class="card-text">{{ product.description }}</p>
                    <p class="card-text">Price: ${{ product.price }}</p>
                    <p class="card-text">Size: {{ product.size }}</p>
                    <p class="card-text">Weight: {{ product.weight }}</p>
                    <p class="card-text">SKU: {{ product.sku }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  const route = useRoute()
  import { ref } from 'vue';
  console.log(route.params.id)
  const product = ref({})

  onMounted(async () => {
      try {
        const response = await fetch(`http://localhost:8000/api/products/${route.params.id}`);
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await response.json();
        console.log(data)
        product.value = data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    });
  </script>
  
  <style scoped>
    img {
        height: 500px;
        object-fit: cover;
    }
  </style>
  
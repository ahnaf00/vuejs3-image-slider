<script setup>
import { ref, reactive } from "vue"

const images = reactive([
  "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
  "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
  "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60",
  "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
]);

let index = ref(0);
const fullImage = ref(images[0]);

function previousImg() {
  index.value--;
  if (index.value < 0) {
    index.value = images.length - 1;
  }
  fullImage.value = images[index.value];
}

function nextImg() {
  index.value++;
  if (index.value >= images.length) {
    index.value = 0;
  }
  fullImage.value = images[index.value];
}
</script>

<template>
  <div class="container">
    <div class="col-lg-12">
      <div class="row d-flex justify-content-center">
        <div id="carouselExampleControls" class="carousel slide w-75">
          <div class="carousel-inner">
            <div class="carousel-item" v-for="(image, idx) in images" :key="idx" :class="{ 'active': idx === index }">
              <img :src="image" class="d-block">
            </div>
          </div>
          <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="prev" @click="previousImg">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
          </button>
          <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="next" @click="nextImg">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.carousel-inner {
  transition: transform 0.5s ease;
}
.carousel-item {
  position: relative;
  transition: opacity 0.5s ease;
}
.carousel-item:not(.active) {
  opacity: 0;
}
</style>


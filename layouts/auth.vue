<template>
    <div class="d-flex vh-100">
      <!-- Left side with image -->
      <div class="w-50 d-none d-md-block">
        <img src="https://via.placeholder.com/600x800" alt="Placeholder Image" class="img-fluid h-100 w-100">
      </div>
      <!-- Right side with form -->
      <div class="w-50 d-flex align-items-center justify-content-center">
        <slot />
      </div>
    </div>
  </template>
  
  <style scoped>
  img {
    object-fit: cover;
  }
  </style>
  
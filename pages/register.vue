<script>
definePageMeta({
  layout: "auth",
});
</script>

<template>
  <div class="d-flex align-items-center justify-content-center vh-100">
    <div class="card p-4" style="width: 100%; max-width: 500px;">
      <h2 class="text-center mb-4">Register</h2>
      <form>
        <div class="mb-3">
          <label for="username" class="form-label">Username</label>
          <input type="text" class="form-control" id="username" placeholder="Enter your username">
        </div>
        <div class="mb-3">
          <label for="email" class="form-label">Email address</label>
          <input type="email" class="form-control" id="email" placeholder="Enter your email">
        </div>
        <div class="mb-3">
          <label for="password" class="form-label">Password</label>
          <input type="password" class="form-control" id="password" placeholder="Enter your password">
        </div>
        <div class="mb-3">
          <label for="confirm-password" class="form-label">Confirm Password</label>
          <input type="password" class="form-control" id="confirm-password" placeholder="Confirm your password">
        </div>
        <div class="d-grid">
          <button type="submit" class="btn btn-primary">Register</button>
        </div>
        <div class="text-center mt-3">
          <router-link to="/login">Already have an account? Login</router-link>
        </div>
      </form>
    </div>
  </div>
</template>


<script setup lang="ts">
useHead({
  title: 'About - My App',
  meta: [
    { name: 'description', content: 'Chào mừng đến với ứng dụng của chúng tôi' }
  ]
})
</script>

<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Header -->
    <AppHeader />

    <!-- Footer -->
    <AppFooter />
  </div>
</template>
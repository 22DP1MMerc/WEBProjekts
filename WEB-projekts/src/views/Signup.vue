<script setup>
  import Foot from '@/components/Foot.vue'
  import NavBar from '@/components/Navbar.vue'
</script>

<template>
    <NavBar />

    <Foot />
</template>

<style>
@media (min-width: 1024px) {
  .main {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
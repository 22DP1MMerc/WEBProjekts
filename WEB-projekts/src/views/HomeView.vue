<script setup>
  import Foot from '@/components/Foot.vue'
  import NavBar from '@/components/Navbar.vue'
</script>

<template>
<NavBar />
    <main>
<img src="https://t4.ftcdn.net/jpg/00/99/82/15/360_F_99821575_nVEHTBXzUnTcLIKN6yOymAWAnFwEybGb.jpg">
    </main>
  <Foot />
</template>

<style>
@media (min-width: 1024px) {
  .main {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
  img {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 40%;
}
}
</style>
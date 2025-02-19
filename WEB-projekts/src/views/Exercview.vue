<script setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  import Foot from '@/components/Foot.vue';
  import NavBar from '@/components/Navbar.vue';
  import Search from '@/components/Search.vue';

  // Reactive state to control the dropdown visibility
  const isDropdownVisible = ref(false);

  // Function to toggle the dropdown visibility
  const toggleDropdown = () => {
    isDropdownVisible.value = !isDropdownVisible.value;
  };

  // Close the dropdown if clicked outside
  const closeDropdown = (event) => {
    if (!event.target.closest('.dropdown')) {
      isDropdownVisible.value = false;
    }
  };

  // Add the event listener when the component is mounted
  onMounted(() => {
    window.addEventListener('click', closeDropdown);
  });

  // Cleanup the event listener when the component is unmounted
  onBeforeUnmount(() => {
    window.removeEventListener('click', closeDropdown);
  });
</script>

<template>
  <NavBar />
  <Search />
  <div class="dropdown">
    <button @click="toggleDropdown" class="dropbtn">Muskuļu grupa</button>
    <!-- Use v-show to show/hide the dropdown based on the isDropdownVisible value -->
    <div v-show="isDropdownVisible" class="dropdown-content">
      <a href="#">Tricepsi</a>
      <a href="#">Bicepsi</a>
      <a href="#">Grudaks</a>
    </div>
  </div>
  <div class="dropdown">
    <button @click="toggleDropdown" class="dropbtn">Ekipējums</button>
    <!-- Use v-show to show/hide the dropdown based on the isDropdownVisible value -->
    <div v-show="isDropdownVisible" class="dropdown-content">
      <a href="#">Hanteles</a>
      <a href="#">Stienis</a>
      <a href="#">Kettlebell</a>
    </div>
  </div>
  <Foot />
</template>

<style scoped>
  .dropdown {
    position: relative;
    justify-content: center ;
    display: flex;

  }

  .dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    z-index: 1;
  }

  /* Display dropdown content when isDropdownVisible is true */
  .dropdown-content a {
    color: black;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
  }

  .dropdown-content a:hover {
    background-color: #f1f1f1;
  }

  /* Show dropdown when toggled */
  .dropdown .dropdown-content {
    display: block;
  }
</style>

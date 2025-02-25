<script setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  import Foot from '@/components/Foot.vue';
  import NavBar from '@/components/Navbar.vue';
  import Search from '@/components/Search.vue';


</script>

<template>
  <NavBar />
  <Search />
  <div class="dropdown-container">
    <div class="dropdown">
      <button @click="toggleDropdown('muscle')" class="dropbtn">Muskuļu grupa</button>
      <div v-show="isDropdownVisible.muscle" class="dropdown-content">
        <a href="#">Tricepsi</a>
        <a href="#">Bicepsi</a>
        <a href="#">Grudaks</a>
      </div>
    </div>
    <div class="dropdown">
      <button @click="toggleDropdown('equipment')" class="dropbtn">Ekipējums</button>
      <div v-show="isDropdownVisible.equipment" class="dropdown-content">
        <a href="#">Hanteles</a>
        <a href="#">Stienis</a>
        <a href="#">Kettlebell</a>
      </div>
    </div>
  </div>
  <Foot />
</template>

<script>
export default {
  data() {
    return {
      isDropdownVisible: {
        muscle: false,
        equipment: false
      }
    };
  },
  methods: {
    toggleDropdown(type) {
      this.isDropdownVisible[type] = !this.isDropdownVisible[type];
    }
  }
};
</script>

<style scoped>
.dropbtn {
  background-color: #ff6600;
  color: white;
  padding: 16px;
  font-size: 16px;
  border: none;
}

/* The container <div> - needed to position the dropdown content */
.dropdown {
  position: relative;
  display: inline-block;
}

/* Dropdown Content (Hidden by Default) */
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

/* Links inside the dropdown */
.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

/* Change color of dropdown links on hover */
.dropdown-content a:hover {background-color: #ddd;}

/* Show the dropdown menu on hover */
.dropdown:hover .dropdown-content {display: block;}

/* Change the background color of the dropdown button when the dropdown content is shown */
.dropdown:hover .dropbtn {background-color: #ff8c3f;}
</style>
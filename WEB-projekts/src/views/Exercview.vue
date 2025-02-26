<script setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  import Foot from '@/components/Foot.vue';
  import NavBar from '@/components/Navbar.vue';
  import Search from '@/components/Search.vue';


</script>

<template>
  <NavBar />
  <Search />
  <div class="container">
    <div class="dropdown-container">
      <div class="dropdown">
        <button @click="toggleDropdown('muscle')" class="dropbtn">
          Muskuļu grupa: {{ selectedMuscle || "Visi" }}
        </button>
        <div v-show="isDropdownVisible.muscle" class="dropdown-content">
          <a href="#" @click.prevent="filterByMuscle('Tricepsi')">Tricepsi</a>
          <a href="#" @click.prevent="filterByMuscle('Bicepsi')">Bicepsi</a>
          <a href="#" @click.prevent="filterByMuscle('Grudaks')">Grudaks</a>
          <a href="#" @click.prevent="filterByMuscle(null)">Visi</a>
        </div>
      </div>

      <div class="dropdown">
        <button @click="toggleDropdown('equipment')" class="dropbtn">
          Ekipējums: {{ selectedEquipment || "Visi" }}
        </button>
        <div v-show="isDropdownVisible.equipment" class="dropdown-content">
          <a href="#" @click.prevent="filterByEquipment('Hanteles')">Hanteles</a>
          <a href="#" @click.prevent="filterByEquipment('Stienis')">Stienis</a>
          <a href="#" @click.prevent="filterByEquipment('Kettlebell')">Kettlebell</a>
          <a href="#" @click.prevent="filterByEquipment(null)">Visi</a>
        </div>
      </div>
    </div>
  </div>
  
    <div class="exercise-list">
      <ul>
        <li v-for="exercise in filteredExercises" :key="exercise.name">
          {{ exercise.name }} ({{ exercise.muscle }} - {{ exercise.equipment }})
        </li>
      </ul>
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
      },
      selectedMuscle: null,
      selectedEquipment: null,
      exercises: [
        { name: "Triceps Dips", muscle: "Tricepsi", equipment: "Hanteles" },
        { name: "Biceps Curl", muscle: "Bicepsi", equipment: "Hanteles" },
        { name: "Bench Press", muscle: "Grudaks", equipment: "Stienis" },
        { name: "Overhead Press", muscle: "Grudaks", equipment: "Kettlebell" },
        { name: "Triceps Extension", muscle: "Tricepsi", equipment: "Stienis" }
      ]
    };
  },
  computed: {
    filteredExercises() {
      return this.exercises.filter(exercise => {
        return (
          (!this.selectedMuscle || exercise.muscle === this.selectedMuscle) &&
          (!this.selectedEquipment || exercise.equipment === this.selectedEquipment)
        );
      });
    }
  },
  methods: {
    toggleDropdown(type) {
      this.isDropdownVisible[type] = !this.isDropdownVisible[type];
    },
    filterByMuscle(muscle) {
      this.selectedMuscle = muscle;
      this.isDropdownVisible.muscle = false;
    },
    filterByEquipment(equipment) {
      this.selectedEquipment = equipment;
      this.isDropdownVisible.equipment = false;
    }
  }
};
</script>

<style scoped>

.container {
  display: flex;
  justify-content: center;
  
}

.dropdown-container {
  display: flex;
  gap: 10px;
}

.dropbtn {
  background-color: #ff6600;
  color: white;
  padding: 16px;
  font-size: 16px;
  border: none;
  min-width: 136px;
}

.dropdown {
  position: relative;
  display: inline-block;
  align-items: center;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  min-width: 136px;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown-content a:hover {background-color: #ddd;}

.dropdown:hover .dropdown-content {display: block;}

.dropdown:hover .dropbtn {background-color: #ff8c3f;}

.exercise-list {
  text-align: center;
  margin-top: 20px;
}

.exercise-list ul {
  list-style: none;
  padding: 0;
}

.exercise-list li {
  margin: 5px 0;
  padding: 10px;
  border-radius: 5px;
}

</style>
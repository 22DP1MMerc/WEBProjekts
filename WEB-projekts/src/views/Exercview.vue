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

    <div class="exercise-list">
      <div v-if="filteredExercises.length" class="cards">
        <div 
          v-for="exercise in filteredExercises" 
          :key="exercise.name" 
          class="exercise-card"
          @click="toggleDetails(exercise)"
        >
          <h3>{{ exercise.name }}</h3>
          <p>{{ exercise.muscle }} - {{ exercise.equipment }}</p>
          
          <div v-if="exercise.showDetails" class="exercise-details">
            <p><strong>Apraksts:</strong> {{ exercise.description }}</p>
            <p><strong>Reps/Sets:</strong> {{ exercise.sets }} komplekti x {{ exercise.reps }} reps</p>
          </div>
        </div>
      </div>
      <p v-else>Nav atrasti vingrinājumi</p>
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
      searchQuery: "",
      exercises: [
        { 
          name: "Triceps Dips", muscle: "Tricepsi", equipment: "Hanteles", 
          description: "Ķermeņa svara vingrinājums, kas stiprina tricepsus.", 
          sets: 3, reps: 12, showDetails: false 
        },
        { 
          name: "Biceps Curl", muscle: "Bicepsi", equipment: "Hanteles", 
          description: "Klasiska hanteles pacelšana bicepsa stiprināšanai.", 
          sets: 3, reps: 10, showDetails: false 
        },
        { 
          name: "Bench Press", muscle: "Grudaks", equipment: "Stienis", 
          description: "Stieņa spiešana guļus, kas trenē krūšu muskuļus.", 
          sets: 4, reps: 8, showDetails: false 
        },
        { 
          name: "Overhead Press", muscle: "Grudaks", equipment: "Kettlebell", 
          description: "Stumšanas kustība virs galvas, kas attīsta plecus un krūšu muskuļus.", 
          sets: 3, reps: 10, showDetails: false 
        },
        { 
          name: "Triceps Extension", muscle: "Tricepsi", equipment: "Stienis", 
          description: "Stieņa pacelšana aiz galvas, izolējot tricepsus.", 
          sets: 3, reps: 12, showDetails: false 
        }
      ]
    };
  },
  computed: {
    filteredExercises() {
      return this.exercises.filter(exercise => {
        return (
          (!this.selectedMuscle || exercise.muscle === this.selectedMuscle) &&
          (!this.selectedEquipment || exercise.equipment === this.selectedEquipment) &&
          exercise.name.toLowerCase().includes(this.searchQuery.toLowerCase())
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
    },
    toggleDetails(exercise) {
      exercise.showDetails = !exercise.showDetails;
    }
  }
};
</script>

<style scoped>


.dropdown-container {
  display: flex;
  gap: 10px;
  justify-content: center;
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

.cards {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.exercise-card {
  background: #f8f8f8;
  padding: 15px;
  border-radius: 8px;
  width: 250px;
  cursor: pointer;
  transition: 0.3s;
  border: 1px solid #ccc;
}

.exercise-card:hover {
  background-color: #e0e0e0;
}

.exercise-details {
  margin-top: 10px;
  text-align: left;
  background: #fff;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

</style>
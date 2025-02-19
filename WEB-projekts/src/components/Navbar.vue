<template>
    <nav>
      <ul>
        <li>
          <a href="/routine" class="nav-link">Routines</a>
        </li>
        <li>
          <a href="/exercise" class="nav-link">Exercises
          </a>
          </li>
        <li>
          <a href="/" class="nav-link">Home</a>
        </li>
        <li>
          <a href="/about" class="nav-link">About</a>
        </li>
        <li>
          <a href="/contacts" class="nav-link">Contact</a>
        </li>
        <li>
          <a href="/login" class="nav-link">Log in</a>
        </li>
        <li>
          <a href="/signup" class="nav-link">Sign up</a>
        </li>
      </ul>
    </nav>
  </template>
  
  <script setup>

  </script>
  

<script setup>
defineProps();

const emit = defineEmits();

const setActiveView = (viewName) => {
  emit('updateActiveView', viewName);  // Emit the active view change to parent
};
</script>

<style scoped>
/* Navbar container */
.navbar {
  background-color: black;
  padding: 14px 30px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
  position: sticky;
  top: 0;
  z-index: 10;
  transition: all 0.3s ease;
}

/* Navigation links list */
.nav-links {
  list-style-type: none;
  display: flex;
  justify-content: space-between;
  gap: 30px;
}

/* Individual nav item */
.nav-links li {
  display: inline-block;
}

/* Navigation link styles */
.nav-link {
  color: #fff;
  text-decoration: none;
  font-size: 16px;
  font-weight: 600;
  padding: 12px 24px;
  transition: all 0.3s ease;
  border-radius: 5px;
  position: relative;
  overflow: hidden;
}



.nav-link:hover::before {
  transform: translate(-50%, -50%) scale(1);
}

.nav-link:hover {
  color: #ffffff;
  border-color: #ffffff;
}

/* Active link styling */
.nav-link.active {
  color: #ffffff; /* Highlight active link */
}

/* Mobile responsiveness */
@media (max-width: 768px) {
  .nav-links {
    flex-direction: column;
    align-items: center;
    gap: 20px;
    margin-top: 10px;
  }
}
</style>
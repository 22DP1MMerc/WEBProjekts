<script setup>
  import Foot from '@/components/Foot.vue'
  import NavBar from '@/components/Navbar.vue'
</script>

<template>
  <main>
<NavBar />
    <main>
        <h2>Labākie treniņu plāni</h2>
        <p>
            Šeit jūs varat atrast labāko vingrinājumus ķermeņu daļām un splitus, kā arī mašīnu lietošanas instrukcijas
        </p>

    </main>
    <aside>
        <h3>Papildu informācija</h3>
        <p>
            Tavs ceļš uz labāku nākotni
        </p>
    </aside>

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
}
</style>
<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
</script>

<template>
  <main>
    <header>
        <h1>Marta treniņi</h1>

        <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/contacts">Contacts</RouterLink>
      </nav>
    </header>
    <main>
        <h2>Labākie treniņu plāni</h2>
        <p>
            Šeit jūs varat atrast labāko vingrinājumus ķermeņu daļām un splitus, kā arī mašīnu lietošanas instrukcijas
        </p>
        <img src="https://www.stockvault.net//data/2016/06/29/203426/thumb16.jpg"
        alt="Tu, ja tu sekosi man">
    </main>
    <aside>
        <h3>Papildu informācija</h3>
        <p>
            Tavs ceļš uz labāku nākotni
        </p>
    </aside>
    <footer>
        <p>Visas tiesības aizsargātas</p>
        <p>@2024</p>
    </footer>
  </main>
</template>

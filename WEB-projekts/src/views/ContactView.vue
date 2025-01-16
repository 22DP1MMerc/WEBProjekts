<template>

<nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/contacts">Contacts</RouterLink>
      </nav>

      <div class="contacts">
    <h1>This is a contacts page</h1>
  </div>

</template>

<style>
@media (min-width: 1024px) {
  .contacts {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
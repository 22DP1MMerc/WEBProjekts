<script setup>
  import Foot from '@/components/Foot.vue'
  import NavBar from '@/components/Navbar.vue'
</script>

<template>
<NavBar />
    <main>
<section class="hero">

      <h2>Build Your Future Today</h2>
      <p>Innovative solutions to elevate your success.</p>

      <button class="cta-button">Get Started</button>
    </section>

    <section class="features">
      <h3>Why Choose Us?</h3>
      <div class="feature-grid">
        <div class="feature-card">
          <h4>🚀 AI-Powered Insights</h4>
          <p>Get smart recommendations based on your data.</p>
        </div>
        <div class="feature-card">
          <h4>🔗 Seamless Integration</h4>
          <p>Easily connect with your favorite tools.</p>
        </div>
        <div class="feature-card">
          <h4>📞 24/7 Support</h4>
          <p>We’re here for you whenever you need help.</p>
        </div>
      </div>
    </section>

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

body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}


.logo {
  font-size: 24px;
  font-weight: bold;
}

.hero {
  text-align: center;
  padding: 100px 10%;
  background-image: url("home_back.webp");
}

.hero h2 {
  font-size: 40px;
  margin-bottom: 10px;
}

.hero p {
  font-size: 18px;
  color: white;
  
}

.cta-button {
  margin-top: 20px;
  padding: 12px 24px;
  font-size: 18px;
  color: white;
  background: #ff5733;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}

.cta-button:hover {
  background: #e64a19;
}

/* Features Section */
.features {
  text-align: center;
  padding: 60px 10%;
}

.features h3 {
  font-size: 28px;
  margin-bottom: 20px;
}

.feature-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}

.feature-card {
  background: #f4f4f4;
  padding: 20px;
  border-radius: 10px;
  width: 300px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.feature-card:hover {
  transform: translateY(-5px);
}

.feature-card h4 {
  font-size: 20px;
  margin-bottom: 10px;
}

</style>
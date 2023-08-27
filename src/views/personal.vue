<template>
    <HomeHead></HomeHead>
    <div class="personal-page">
      <header>
        <h1>{{ fullName }}</h1>
        <p>{{ occupation }}</p>
      </header>
      <main>
        <section>
          <h2>关于我</h2>
          <p>{{ bio }}</p>
        </section>
        <section>
          <h2>联系我</h2>
          <p>Email: {{ email }}</p>
          <p>Phone: {{ phone }}</p>
        </section>
      </main>
    </div>
  </template>
  
  <script setup>
  import HomeHead from "../components/header.vue";

    const fullName =  "Jone Snow";
    const occupation = "China/student";
    const bio = "臭要饭的......";
    const email = "youremail@example.com";
    const phone = "123-456-7890";

  </script>
  
  <style scoped>
  .personal-page {
    font-family: Arial, sans-serif;
    margin: 50px;
    text-align: center;
  }
  
  header {
    margin-bottom: 40px;
  }
  
  h1 {
    margin: 0;
  }
  
  section {
    margin-bottom: 40px;
  }
  
  h2 {
    font-size: 1.5rem;
    margin-bottom: 10px;
  }
  
  p {
    font-size: 1.1rem;
  }
  </style>
  
<template>
    <header class="blog-header">
      <div class="logo">
        <!-- <router-link to="/"> -->
          <h1>{{ siteName }}</h1>
        <!-- </router-link> -->
      </div>
    </header>
</template>
  
  
<script setup>
    const siteName = 'You Blog'; 
</script>
  
  
<style scoped>
    .blog-header {
      background-color: #222;
      color: white;
      padding: 10px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    
    .logo {
      font-size: 24px;
      margin-bottom: 10px;
    }
</style>


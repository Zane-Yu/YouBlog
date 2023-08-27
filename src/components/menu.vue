<template>
    <header class="blog-header">
      <div class="menu">
      <a
          v-for="(value, index) in menuItems"
          :key="index"
          :class="{ active: activeIndex === index }"
          @click="changeActive(index)"
      >
          {{ value }}
      </a>
      <router-link to="/personal"><a>>> 个人主页</a></router-link>
      </div>
    </header>
    
</template>
  
<script setup>
    import { ref } from 'vue';
    const emit = defineEmits();
    
    const menuItems = ['广场', '搜索', '发博']; 
    
    const activeIndex = ref(0);
    const changeActive = (index) => {
        activeIndex.value = index;
        emit('menuClick', activeIndex.value);
    };
    
</script>

<style scoped>
.blog-header {
  background-color: #222;
  color: white;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 40px;
}
.menu {
    display: flex;
    gap: 30px;
  }
  
  .menu a {
    text-decoration: none;
    color: white;
    padding: 10px 20px;
    font-size: 20px;
    transition: color 0.3s;
  }
  
  .menu a.active {
    color: black;
    font-weight: bolder;
    background-color: white;
    border-radius: 5px;
    padding: 10px 20px;
  }
</style>
  
<template>
  <HomeHead />
  <HomeMenu @menuClick="handleMenuClick"></HomeMenu>

  <KeepAlive>
    <component :is="tabComponent" 
              :blogObj="blogs"
              @blogClick="handleBlogClick">
    </component>
  </KeepAlive>
</template>


<script setup>
import { RouterLink, RouterView } from 'vue-router';
import { ref, reactive } from 'vue';

import HomeHead from "../components/header.vue";
import HomeMenu from "../components/menu.vue";
import BlogEditor from "../components/blog.vue";
import Square from "../components/square.vue";
import Search from "../components/search.vue";

const blogs = reactive({});   /* record the blogs */
const tabComponent = ref(Square);
const handleMenuClick = (data) => {
  if(data === 2){
    tabComponent.value = BlogEditor;
  }
  else if(data === 0){
    tabComponent.value = Square;
  }
  else if(data === 1){
    tabComponent.value = Search;
  }
  else{
    tabComponent.value = null;
  }
};

const handleBlogClick = (title, content) => {
  blogs[title] = content;
  console.log("received:", title, content)
}


</script>


<style scoped>
</style>

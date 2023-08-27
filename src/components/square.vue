<template>
    <div class="blocks-container">
      <p v-if="isEmpty" id="text">空空如也</p>

      <div
        v-for="(content, title, index) in blogObj"
        :key="title"
        class="block"
      >
        <h3>{{ title }}</h3>
        <p>{{ content }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps, computed } from 'vue';
  
  const props = defineProps({
    blogObj: Object,
  });
  const isEmpty = computed(() => {
    return !props.blogObj || Object.keys(props.blogObj).length === 0;
  });

  </script>
  
  <style scoped>
  .blocks-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 60%;
    margin: 0 auto; 
  }
  
  .block {
    width: calc(40% - 20px); 
    margin: 10px;
    padding: 10px;
    border: 2px solid #868686;
    border-radius: 8px;
    background-color: rgb(238, 238, 238);
    justify-content: center;
    text-align: center;
  }

  #text {
    color: gray;
    font-size: 30px;
    font-family: 'Times New Roman', Times, serif;
  }
  </style>
  
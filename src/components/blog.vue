<template>
    <div class="blog-editor">
      <input v-model="blogTitle" placeholder="输入博文标题">
      <textarea v-model="blogContent" placeholder="在这里编辑你的博文"></textarea>
      <button @click="sendBlog">发送博文</button>
      <p v-if="isEmpty">标题和内容都不能为空</p>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  const emit = defineEmits();
  
  const blogTitle = ref('');
  const blogContent = ref('');
  
  const isEmpty = computed(() => blogTitle.value === '' || blogContent.value === '');
  
  const sendBlog = () => {
    if (!isEmpty.value) {
      emit('blogClick', blogTitle.value, blogContent.value);
      // console.log("send:", blogTitle.value, blogContent.value)
      blogTitle.value = '';
      blogContent.value = '';
    }
  };
  </script>
  
  <style scoped>
  .blog-editor {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    flex-direction: column;
    width: 30%; 
    margin: 0 auto; 
    
  }
  
  input, textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    border-radius: 5px;
    font-size: 16px;
  }

  input {
    height: 30px;
  }
  
  textarea {
    height: 180px;
  }

  button {
    background-color: #222;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    font-size: large;
    border-radius: 5px;
  }

  button:hover {
    background-color: rgb(80, 152, 80);
  }
  
  p {
    color: red;
  }
  </style>
  
<template>
    <div class="blocks-container">
        <div class="search-container">
            <input
                v-model="searchQuery"
                placeholder="输入搜索关键词"
                class="search-input"
            />
            <button @click="search" class="search-button">
              <img src="../assets/search.svg">
              搜索
            </button>
        </div>
        <div
            v-for="(content, title) in search_blogs"
            :key="title"
            class="block"
        >
            <h3>{{ title }}</h3>
            <p>{{ content }}</p>
        </div>
    </div>
    <p v-if="isEmpty" id="text">空空如也</p>
</template>
  
<script setup>
    import { defineProps, ref, reactive, computed } from 'vue';
    /* data from the hoem page */
    const props = defineProps({
        blogObj: Object,
    });

    /* search function */
    const searchQuery = ref('');
    const search_blogs = reactive({});
    const search = () => {
        if(searchQuery.value === ''){
            return;
        }
        console.log("rearch:", searchQuery.value);
        const searchRegex = new RegExp(searchQuery.value, 'i');
        Object.keys(search_blogs).forEach(key => delete search_blogs[key]);
        for (const title in props.blogObj) {
            if (searchRegex.test(title)) {
                search_blogs[title] = props.blogObj[title];
            }
        }
        console.log(search_blogs);
        searchQuery.value = "";
    };

    const isEmpty = computed(() => {
        return !search_blogs || Object.keys(search_blogs).length === 0;
    });
</script>
  
<style scoped>
  .blocks-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 30%;
    margin: 0 auto; 
  }
  
  .block {
    width: 100%;
    margin: 10px;
    padding: 10px;
    border: 2px solid #868686;
    border-radius: 8px;
    background-color: rgb(238, 238, 238);
    justify-content: center;
    text-align: center;
  }
  .search-container {
    display: flex;
    align-items: center;
    margin: 20px;
  }
  
  .search-input {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    flex: 1;
    margin-right: 10px;
    height: 24px;
    font-size: large;
  }
  
  .search-button {
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: large;
    display: flex;
  }

  .search-button img{
    margin-right: 6px;
    padding: 0;
    width: 23px;
    color: white;
  }

  #text {
    color: gray;
    font-size: 30px;
    font-family: 'Times New Roman', Times, serif;
    justify-content: center;
    text-align: center;
  }
</style>
  
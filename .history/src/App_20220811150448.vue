<script setup>
import { ref } from "@vue/reactivity";


let toggle = ref(false);
let article_arr = ref([]);
let title_arr = ref([]);

const handleSubmit = () =>{
  article_arr.push(title);
  title_arr.push(content);

  console.log(article_arr)
  console.log(title_arr)
}

</script>

<template>
  <h1>sample</h1>

  <button type="button" v-on:click="toggle = true">Create new article</button>

  <div class="article" v-if="toggle" >
    inside article
    <form @submit.prevent="handleSubmit()">
      <label for="title"> Article Title</label>
      <input type="text"  name="title" v-model="title">

      <label for="content"> Article content</label>
      <input type="text" name="content" v-model="content">

      <button type="submit" >submit</button>

    </form>

  </div>

</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
.article {
  background-color: aquamarine;
  width: 50%;
  margin: auto;
  color:black;
}
</style>

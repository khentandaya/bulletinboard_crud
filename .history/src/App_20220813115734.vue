<script setup>
import { reactive, ref } from "@vue/reactivity";

let toggle = ref(false);
let toggle_edit = ref(false);

const article_arr = ref([]);
const title = ref("");
const content = ref("");

//post_info
const handleSubmit = () => {
  article_arr.value = [
    ...article_arr.value,
    {
      title: title.value,
      content: content.value,
      id: Math.floor(Math.random() * 100000),
      created_at: Date.now(),
    },
  ];

  title.value = "";
  content.value = "";

  console.log(article_arr.value);
};

//delete_info
const deleteArticle = (itemID) => {
  let i = article_arr.value.map((item) => item.id).indexOf(itemID);
  article_arr.value.splice(i, 1);
};

//edit_info
const editArticle = (itemID) => {
  toggle_edit = "true";
  let i = article_arr.value.map((item) => item.id).indexOf(itemID);

  console.log(article_arr.value[i]);
  console.log(i);
};
</script>

<template>
  <h1>sample</h1>

  <button type="button" v-on:click="toggle = true">Create new article</button>

  <div class="article" v-if="toggle">
    inside article
    <form @submit.prevent="handleSubmit()">
      <label for="title"> Article Title</label>
      <input aria-label="Article Title" type="text" v-model="title" />

      <label for="content"> Article content</label>
      <input aria-label="Article Content" type="text" v-model="content" />

      <button type="submit">submit</button>
    </form>
  </div>
  <div class="table">
    <table>
      <tr v-for="article in article_arr" :key="article.id">
        <td>Article:{{ article.title }} Content:{{ article.content }}</td>
        <td>
          <button type="button" @click="deleteArticle(article.id)">delete</button>
        </td>
        <td>
          <button type="button" @click="editArticle(article.id)">edit</button>
        </td>
      </tr>
    </table>
  </div>
  <div class="edit-container" v-if="toggle_edit">
    <input aria-label="Title" type="text" />
    <input aria-label="Content" type="text" />

    <button type="button" @click="updateArticle()"></button>
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
  color: black;
}

.edit-container {
  background-color: aquamarine;
  width: 50%;
  margin: auto;
  color: black;
}
</style>

<script setup>
import { ref } from "@vue/reactivity";


let toggle = ref(false);

const handleClick = () =>{
  toggle = true;

}

</script>

<template>
  <h1>sample</h1>

  <button type="button" v-on:click="toggle = true">Create new article</button>

  <div class="article" v-if="toggle" >
    inside article
    <form>
      <label for="title"> Article Title</label>
      <input type="text"  name="title">

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

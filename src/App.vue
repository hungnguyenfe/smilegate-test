<script setup lang="ts">
import Header from "./components/Header.vue";
import Card, {Item} from "@/components/Card.vue";
import {onBeforeMount, ref} from "vue";

const list = ref<Item[]>();

function randomInt(min: number, max: number) {
  return Math.floor(Math.random() * (max - min + 1) + min);
}

function mockupListData(length: number) {
  list.value = new Array(length).fill(0).map((_) => {
    const index = randomInt(0, 1);
    const url = index
        ? 'https://i.imgur.com/2MM9Jqo.png'
        : 'https://i.imgur.com/unmma82.jpeg'
    const title = 'Product name is quite long in some cases.'

    return {
      url,
      title
    }
  })
}

onBeforeMount(() => {
  mockupListData(20);
})
</script>

<template>
  <div>
    <Header/>

    <section class="section container">
      <h2 class="section-title">Photo Cards:</h2>

      <div class="section-cards">
        <Card v-for="item in list" :item="item" :key="item.url"/>
      </div>
    </section>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/common/breakpoints" as *;

.section {
  display: flex;
  flex-direction: column;
  gap: 1tem;

  &-title {
    font-size: 1.5rem;
    font-weight: bold;
    margin-bottom: 20px;
  }

  &-cards {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;

    @include md {
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    }

    @include lg {
      grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
    }
  }
}
</style>

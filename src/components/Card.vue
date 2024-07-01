<script lang="ts" setup>
export interface Item {
  url: string;
  title: string;
}

defineProps<{item: Item}>()
</script>

<template>
  <div class="card">
    <div class="card-img">
      <img :src="item.url" :alt="item.title">
    </div>
    <p class="card-title truncate">
      {{ item.title }}
    </p>
  </div>
</template>

<style lang="scss" scoped>
@use "@/assets/styles/common/variables" as *;

.card {
  box-shadow: $shadow;

  &-img {
    position: relative;
    padding-bottom: calc(100%/3*2);

    img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  &-title {
    padding: 10px;
    font-weight: bold;
  }
}
</style>
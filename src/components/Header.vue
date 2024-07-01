<template>
  <header>
    <nav class="container">
      <a href="/" class="logo">
        <img src="../assets/images/logo.png" alt="Logo">
      </a>

      <ul class="menu">
        <li class="menu-link">Indie Game</li>
        <li class="menu-link">Entry Game</li>
        <li class="menu-link">Community</li>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
@use "@/assets/styles/common/variables" as *;
@use "@/assets/styles/common/breakpoints" as *;

header {
  background: map-get($colors, header);
  text-align: center;

  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
  }
}

.logo {
  max-width: 100px;

  img {
    width: 100%;
    height: auto;
  }
}

.menu {
  display: none;
  @include sm {
    display: flex;
    gap: 1rem;
  }

  &-link {
    list-style: none;
    border: 1px solid white;
    border-radius: 0.25rem;
    padding: 0.5rem 1rem;
    color: map-get($colors, light);
    cursor: pointer;
    transition: border .3s, color .3s;

    &:hover {
      color: map-get($colors, dark);
      border-color: map-get($colors, dark);
    }
  }

}
</style>
<template>
  <div class="app__header">
      <div class="header container">
          <h1 class="header"><RouterLink to="/" class="header">FakeStore</RouterLink></h1>
          <button class="app_header_button button"></button>
      </div>
  </div>
</template>

<style>
.app__header {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #c1a90d;
  margin-bottom: 20px;
}

.header {
  color: #000;
}

.header.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 1140px;
}

.app_header_button.button {
  width: 40px;
  height: 40px;
  background-color: transparent;
  background-image: url('/public/cart.svg');
  background-position: center;
  background-size: contain;
  border: none;
  cursor: pointer;
}
</style>

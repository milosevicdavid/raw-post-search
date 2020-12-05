<template>
  <div  class="card">
    <div class="card-wrapper">
      <span class="card-title"
        ><h1>{{ item.title }}</h1></span
      >
      <span class="card-body">{{ `${item.body}.` }}</span>
    </div>
  </div>
  </template>

<script>
export default {
  props: ["item"],
};
</script>

<style lang="scss">

.card {
  display: flex;
  justify-content: center;
  align-items: center;

  &-wrapper {
    width: 50vw;
    margin-top: 50px;

    @media (max-width: 576px) {
      width: 80vw;
    }
  }

  &-title {
    display: block;
    text-transform: capitalize;
    background-color: #69c28e;
    padding: 20px;
    color: #fff;
    border-radius: 20px 20px 0 0;
  }

  &-body {
    display: block;
    background-color: #6fce96;
    padding: 20px;
    border-radius: 0 0 20px 20px;
    font-weight: 500;
    color: #fff;
    font-size: 16px;

    &::first-letter {
      text-transform: capitalize;
    }
  }
}
</style>


<script setup>
import HeaderComp from "@/components/template/HeaderComp.vue";
import RodapéComp from "./components/template/RodapéComp.vue";
</script>
<template>
  <HeaderComp />
  <main>
    <RouterView />
  </main>
  <RodapéComp />
</template>

<style>
@import "@/assets/base.css";
@import "@/assets/style.css";

#app {
  margin: 0 auto;
  height: 100vh;

  font-weight: normal;
}
header,
footer {
  background: rgb(121, 33, 133);
  color: rgb(0, 0, 0);
  font-size: 1.3rem;
  height: 15%;
  display: flex;
  align-items: center;
  padding-left: 2rem;
}
a {
  color: white;
  text-decoration: none;
}
main {
  height: 70%;
}
</style>

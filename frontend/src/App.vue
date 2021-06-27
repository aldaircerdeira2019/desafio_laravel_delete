<template>
  <div id="app">
    <Header></Header>
    <div class="container">
      <div class="column is-8 is-offset-2">
        <router-view />
      </div>
    </div>
  </div>
</template>
<script>
import Header from "./views/components/Header.vue";

export default {
  components: { Header },
};
</script>

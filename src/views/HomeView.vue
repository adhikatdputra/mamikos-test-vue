<template>
  <div class="home">
    <div class="main-container">
      <div class="heading">
        Search the name of your favorite national team player
      </div>
      <Search />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Search from "@/components/SearchBar.vue";

export default {
  name: "HomeView",
  components: {
    Search,
  },
};
</script>

<style lang="scss" scoped>
.home {
  position: relative;
  padding: 2rem 0;
  .main-container {
    max-width: 414px;
    margin: 0 auto;
    border: 1px solid #eaeaea;
    width: 100%;
    position: relative;
    padding: 20px;
    border-radius: 16px;
    box-shadow: 2px 10px 13px 0px rgba(0, 0, 0, 0.108);

    .heading {
      font-size: 24px;
      font-weight: 700;
      padding-bottom: 16px;
    }
  }
}
</style>

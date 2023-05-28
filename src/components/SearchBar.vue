<template>
  <div class="search-area">
    <form>
      <input
        type="text"
        v-model="searchText"
        class="input-field"
        placeholder="Search here..."
      />
    </form>
    <ul v-if="isLoading">
      <li>Loading...</li>
    </ul>
    <ul v-else-if="filteredNames.length > 0">
      <li
        :class="{ 'odd-item': index % 2 === 0, 'even-item': index % 2 !== 0 }"
        v-for="(name, index) in filteredNames"
        :key="name"
      >
        {{ name }}
      </li>
    </ul>
    <div v-else>
      <p v-if="isSearch">No names found</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isLoading: false,
      names: [
        "Witan Sulaeman",
        "Marc Klok",
        "Fachruddin Aryanto",
        "Asnawi Mangkualam",
        "Jordi Amat",
        "Pratama Arhan",
        "Elkan Baggott",
        "Sandy Walsh",
        "Marselino Ferdinan",
        "Stefano Lilipaly",
        "Rachmat Arianto",
        "Egy Maulana Vikri",
      ],
      searchText: "",
      isSearch: false,
    };
  },
  watch: {
    searchText() {
      this.isLoading = true;
      setTimeout(() => {
        this.isLoading = false;
      }, 300);
    },
  },
  computed: {
    filteredNames() {
      if (this.searchText === "") {
        this.isSearching(false);
        return "";
      }
      this.isSearching(true);
      const searchTextLower = this.searchText.toLowerCase();
      const result = this.names.filter((name) =>
        name.toLowerCase().includes(searchTextLower)
      );
      return result.length > 0 ? result : [];
    },
  },
  methods: {
    isSearching(bool) {
      this.isSearch = bool;
    },
  },
};
</script>

<style lang="scss" scoped>
.search-area {
  padding: 16px 30px;
  .input-field {
    width: 100%;
    padding: 12px;
    border-radius: 8px;
    border: 1px solid #a0a0a0;
    display: block;
    position: relative;
    box-sizing: border-box;
    font-weight: 500;
    font-family: "Plus Jakarta Sans", sans-serif;
  }

  ul {
    list-style-type: none;
    padding-left: 0;

    li {
      padding: 8px;
    }
    .odd-item {
      background-color: #eaeaea;
    }

    .even-item {
      background-color: #f3f3f3;
    }
  }
}
</style>

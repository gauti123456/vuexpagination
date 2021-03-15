<template>
  <div class="pagination">
    <!-- показываем пагинатор только если есть карточки -->
    <div v-if="totalPages() > 0" class="pagination__buttons">
      <span
        v-if="showPreviousLink()"
        @click="updatePage(currentPage - 1)"
        class="pagination__btn"
      >back</span>
      <span class="pagination__buttons--center">{{currentPage +1}} / {{totalPages()}}</span>
      <span
        v-if="showNextLink()"
        @click="updatePage(currentPage + 1)"
        class="pagination__btn"
      >forward</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "Pagination",
  props: ["cards", "currentPage", "pageSize"],
  methods: {
    updatePage(pageNumber) {
      this.$emit("pageUpdate", pageNumber);
    },
    totalPages() {
      //делим длину на количество в странице и ceil чтобы не было дробных значений
      return Math.ceil(this.cards.length / this.pageSize);
    },
    showPreviousLink() {
      return this.currentPage === 0 ? false : true;
    },
    showNextLink() {
      return this.currentPage === this.totalPages() - 1 ? false : true;
    }
  }
};
</script>

<style>
.pagination {
  width: 100%;
}
.pagination__buttons {
  display: flex;
  justify-content: center;
  width: 200px;
  border: 1px solid purple;
  margin: 10px auto;
}
.pagination__buttons--center {
  padding: 0px 20px;
}
</style>

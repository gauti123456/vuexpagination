<template>
  <div class="list">
    <div v-for="(card, index) in visibleCards" :key="index" class="list__item">
      <h3>{{card.title}}</h3>
      <p>{{card.body}}</p>
    </div>
    <Pagination
      :cards="cards"
      @pageUpdate="updatePage"
      :currentPage="currentPage"
      :pageSize="pageSize"
    />
  </div>
</template>
<script>
import Pagination from "./Pagination.vue";
export default {
  name: "List",
  components: {
    Pagination
  },
  data() {
    return {
      currentPage: 0,
      pageSize: 4,
      visibleCards: [],
      cards: [
        {
          title: "title1",
          body: "someText1",
          id: 1
        },
        {
          title: "title2",
          body: "someText2",
          id: 2
        },
        {
          title: "title3",
          body: "someText3",
          id: 3
        },
        {
          title: "title4",
          body: "someText4",
          id: 4
        },
        {
          title: "title5",
          body: "someText5",
          id: 5
        },
        {
          title: "title6",
          body: "someText6",
          id: 6
        },
        {
          title: "title7",
          body: "someText7",
          id: 7
        },
        {
          title: "title8",
          body: "someText8",
          id: 8
        },
        {
          title: "title9",
          body: "someText9",
          id: 9
        },
        {
          title: "title10",
          body: "someText10",
          id: 10
        },
        {
          title: "title11",
          body: "someText11",
          id: 11
        },
        {
          title: "title12",
          body: "someText12",
          id: 12
        },
        {
          title: "title13",
          body: "someText13",
          id: 13
        },
        {
          title: "title14",
          body: "someText14",
          id: 14
        }
      ]
    };
  },
  beforeMount: function() {
    this.updateVisibleCards();
  },
  // computed: {
  //   cards() {
  //     return this.$store.getters.cards;
  //   }
  // },
  methods: {
    updatePage(pageNumber) {
      this.currentPage = pageNumber;
      this.updateVisibleCards();
    },
    updateVisibleCards() {
      this.visibleCards = this.cards.slice(
        this.currentPage * this.pageSize,
        this.currentPage * this.pageSize + this.pageSize
      );
      //если нет карточек
      if (this.visibleCards == 0 && this.currentPage > 0) {
        this.updatePage(this.currentPage - 1);
      }
    }
  }
};
</script>
<style>
* {
  list-style-type: none;
}
.list {
  display: flex;
  flex-wrap: wrap;
  width: 610px;
  justify-content: space-between;
  border: 5px solid orange;
}
.list__item {
  border: 1px solid red;
  width: 300px;
  height: 300px;
}
</style>

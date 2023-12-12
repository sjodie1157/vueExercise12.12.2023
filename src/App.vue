<template>
  <div class="wrapper">
    <div class="row">
      <div class="prodCard" v-for="item in filteredItems" :key="item.id">
        <div class="card-header">
          <h3>{{ item.name }}</h3>
        </div>
        <div class="card-body">
          <img :src="item.imgLink" alt="pic" loading="lazy">
          <p>R {{ item.price }}</p>
        </div>
        <div class="card-footer">
          <a href="#" type="button">View Detail</a>
        </div>
      </div>
        <h2 v-show="filteredItems == 0">No Products</h2>
      </div>
      </div>
      <button type="button" @click="filterItemsByCategory('Suit')">Suits</button>
      <button type="button" @click="filterItemsByCategory('Tuxido')">Tuxedo</button>
      <input type="text" v-model="searchText" @input="filterByName">
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          id: 1,
          name: "Mr Brown",
          category: "Tuxido",
          colour: "Brown",
          price: 2500,
          designer: "Gucci",
          imgLink: "https://i.postimg.cc/RFWNwJpn/Buy-Men-Brown-Wedding-Suit-3-Piece-Formal-Fashion-Party-Wear-Online-in-India-Etsy.jpg",
          quantity: 1
        },
        {
          id: 2,
          name: "Blue Blaze",
          category: "Suit",
          colour: "Blue",
          price: 3607,
          designer: "Prada",
          imgLink: "https://i.postimg.cc/76jb9Pjt/download.jpg",
          quantity: 1
        },
        {
          id: 3,
          name: "Gale chick",
          category: "Tuxido",
          colour: "Red",
          price: 7200,
          designer: "Gucci",
          imgLink: "https://i.postimg.cc/MpwMgTHh/Gale-Chic-Deep-Red-Peaked-Lapel-Double-Breasted-Striped-Business-Suits.jpg",
          quantity: 1
        },
        {
          id: 4,
          name: "Kent Dark",
          category: "Suit",
          colour: "Grey",
          price: 9300,
          designer: "Givenchy",
          imgLink: "https://i.postimg.cc/RhfhD5BS/Kent-Dark-Green-3-Pieces-Peaked-Lapel-One-Button-Business-Suits.jpg",
          quantity: 1
        },
        {
          id: 5,
          name: "Regan",
          category: "Suit",
          colour: "Black",
          price: 9300,
          designer: "Givenchy",
          imgLink: "https://i.postimg.cc/T3cLx6Wh/Regan-Traditional-All-Black-Peaked-Lapel-Double-Breasted-Tailored-Business-Suits-For-Men.jpg",
          quantity: 1
        }
      ],
      filteredItems: []
    }
  },
  computed: {
    categories() {
      return Array.from(new Set(this.items.map((item) => item.category)));
    }
  },
  methods: {
    filterItemsByCategory(category) {
      this.filteredItems = this.items.filter((item) => item.category === category)
    },
    filterByName() {
      this.filteredItems = this.items.filter((item) =>
        item.name.toLowerCase().includes(this.searchText.toLowerCase())
      )
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper .row {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.prodCard {
  width: 18rem;
}

.prodCard>*:is(img) {
  width: 100%;
  aspect-ratio: 1/1;
}

.expensive {
  font-weight: bolder;
  color: darkkhaki;
}

.cheap {
  color: black;
}

img[alt=pic] {
  width: 250px;
  aspect-ratio: 1/1.5;
}
</style>

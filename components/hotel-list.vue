<template>
  <div>
    <div class="row">
      <div class="leftcolumn">
        <div v-if="searchHotel.length !== 0">
        <div class="card" v-for="hotel in searchHotel" :key="hotel.id">
          <div class="cardImg">
            <div class="grid-item item1">
              <img
                src="https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg"
              />
            </div>
            <div  class="grid-item item2">
              <h3>{{hotel.name}}</h3>
              <p>
                <span class="fa fa-star checked"></span>
                <span class="fa fa-star checked"></span>
                <span class="fa fa-star checked"></span>
                <span class="fa fa-star"></span>
                <span class="fa fa-star"></span>
              </p>
              <p>
                {{hotel.address}}, {{hotel.state}}, {{hotel.country_code}}
              </p>
            </div>
            <div class="grid-item item3">
              <button>Show Details</button>
            </div>
          </div>
        </div>
        </div>
        
        <div v-else>
          <h1>There are no hotels for this locations</h1>
        </div>
         <infinite-loading @infinite="infiniteHandler"></infinite-loading>
      </div>
      <div v-if="searchHotel.length !== 0" class="rightcolumn">
        <div class="card">
          <h2>Filter Box</h2>
          <h4>Filter by Name:</h4>
          <p><input type="text" /></p>

          <h2>Filter by rating</h2>
          <h4>Filter by Name:</h4>
          <p>
            <span class="fa fa-star checked"></span>
            <span class="fa fa-star"></span>
            <span class="fa fa-star"></span>
            <span class="fa fa-star"></span>
            <span class="fa fa-star"></span>
          </p>
          <p>
            <span class="fa fa-star checked"></span>
            <span class="fa fa-star"></span>
            <span class="fa fa-star"></span>
            <span class="fa fa-star"></span>
          </p>
          <p>
            <span class="fa fa-star checked"></span>
            <span class="fa fa-star"></span>
            <span class="fa fa-star"></span>
          </p>
          <p>
            <span class="fa fa-star checked"></span>
            <span class="fa fa-star"></span>
          </p>
          <p><span class="fa fa-star checked"></span></p>
        </div>
      </div>
    </div>
    <div class="grid-item item3">
      <button v-on:click="goBack()" style="margin-left: 535px;">Back</button>
    </div>
  </div>
</template>

<script>
import InfiniteLoading from 'vue-infinite-loading';

export default {
  components: {
   InfiniteLoading,
  },
  data() {
    return {
       hotelsList:[],
       destination:'',
    };
  },

  computed: {
    searchHotel() {
     let se = []
     if(this.destination !== '') {
      se = this.hotelsList.filter(p => 
        p.city.toLowerCase().includes(this.destination.toLowerCase())
      )
     } else {
      se = this.hotelsList
     }
     return se
    }
  },

  created() {
   this.destination = localStorage.getItem('cityName');
   
  // alert(this.destination)

    this.getHotelsList();
      console.log('Hotel list');
      console.log(this.hotelsList );
  },

  methods: {
    goBack() {
      this.$emit("getHotelList", false);
    },

     infiniteHandler($state) {
      setTimeout(() => {
        const temp = [];
        for (let i = this.searchHotel.length + 1; i <= this.searchHotel.length + 10; i++) {
          temp.push(i);
        }
        this.searchHotel = this.searchHotel.concat(temp);
        $state.loaded();
      }, 1000);
    },
  

    getHotelsList() {
      fetch("hotels.json")
        .then((response) => response.json())
        .then((data) => (this.hotelsList = data));
    },
    
  },
};
</script>



<style scoped>
.checked {
  color: orange;
}
* {
  box-sizing: border-box;
}

/* Add a gray background color with some padding */
body {
  font-family: Arial;
  padding: 20px;
  background: #f1f1f1;
}

/* Header/Blog Title */
.header {
}

/* Create two unequal columns that floats next to each other */
/* Left column */
.leftcolumn {
  float: right;
  width: 75%;
}

/* Right column */
.rightcolumn {
  float: left;
  width: 25%;
  padding-right: 20px;
}

/* Fake image */
.fakeimg {
  background-color: #aaa;
  width: 100%;
  padding: 20px;
}

/* Add a card effect for articles */
.card {
  background-color: white;
  padding: 20px;
  margin-top: 20px;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Footer */
.footer {
  padding: 20px;
  text-align: center;
  background: #ddd;
  margin-top: 20px;
}

/* Responsive layout - when the screen is less than 800px wide, make the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 800px) {
  .leftcolumn,
  .rightcolumn {
    width: 100%;
    padding: 0;
  }
}

.header {
  background-color: #333;
  display: flex;
  justify-content: space-between;
}
.header ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

.header li {
  float: left;
}

li a {
  display: inline-block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover {
  background-color: #111;
}

.active {
  background-color: red;
}

.logo {
  font-size: 20px;
  color: white;
  display: inline-block;
  padding: 10px 15px;
  text-decoration: none;
}
.card {
}
.cardImg {
  border: solid 1px #ccc;
  padding: 20px;
  display: grid;
  grid-template-columns: 1fr 6fr 1fr;
  gap: 20px;
  align-items: center;
}
.cardImg img {
  max-width: 200px;
}

.rightcolumn .card input {
  width: 100%;
  padding: 10px 15px;
}
</style>

</style>
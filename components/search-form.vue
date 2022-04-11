<template>
  <div>
    <div class="header">
      <a href="#" class="logo"><i class="fa-regular fa-bars"></i> TRAVOLTA</a>
      <ul>
        <li><a href="#home" class="active">About Us</a></li>
        <li><a href="#news">My Bookings</a></li>
        <li><a href="#about">Sign In</a></li>
      </ul>
    </div>
    <div class="row">
      <div class="leftcolumn">
        <div class="card">
          <div class="cardImg">
            <form @submit.prevent="getHotels">
              <div class="d-flex">
                <div>
                  <label>Destination</label>
                  <Dropdown
                    :options="destinations"
                    v-on:selected="validateSelection"
                    v-on:filter="getDropdownValues"
                    :disabled="false"
                    name="zipcode"
                    :maxItem="10"
                    placeholder="Please select an option"
                  >
                  </Dropdown>
                  <label
                    v-if="!isCitySelected"
                    style="color: red; font-weight: bold"
                    >Destination is required</label
                  >
                </div>
                <div>
                  <label>Check-In</label>
                  <date-picker
                    v-model="checkedInDate"
                    valueType="format"
                  ></date-picker>
                  <label
                    v-if="!isCheckinDateSelected"
                    style="color: red; font-weight: bold"
                    >Check-In date is required</label
                  >
                </div>
                <div>
                  <label>Check-Out</label>
                  <date-picker
                    v-model="checkedOutDate"
                    valueType="format"
                  ></date-picker>
                  <label
                    v-if="!isCheckOutDateSelected"
                    style="color: red; font-weight: bold"
                    >Check-Out date is required</label
                  >
                </div>
                <div class="adults">
                  <label>Adults</label>
                  <input type="text" v-model="noOfAdults" />
                </div>
                <div class="adults">
                  <label>Childrens</label>
                  <input type="text" v-model="noOfChildrens" />
                </div>
                <div>
                  <button type="submit">SEARCH</button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div v-for="search in recentSearches" :key="search"  v-on:click="getCurrentSearch(search)" class="column">
        <div class="card">
          <h3> City : {{search.destination}}</h3>
          <p>Check in : {{search.checkinDate}}</p>
          <p>Check out : {{search.checkOutDate}}</p>
          <p>Adults : {{search.adults}}</p>
          <p>Childrens : {{search.childrens}}</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import VeeValidate from "vee-validate";
import Dropdown from "vue-simple-search-dropdown";
import DatePicker from "vue2-datepicker";
import "vue2-datepicker/index.css";

export default {
  layout: "travelta",
  components: {
    Dropdown,
    DatePicker,
    VeeValidate,
  },
  data() {
    return {
      show: false,
      destinations: [],
      city: "",
      selected: { name: null, id: null },
      checkedInDate: null,
      checkedOutDate: null,
      noOfAdults: 0,
      noOfChildrens: 0,
      isCitySelected: true,
      isCheckinDateSelected: true,
      isCheckOutDateSelected: true,
      recentSearches: [],
    };
  },

  created() {
     this.recentSearches = JSON.parse(localStorage.getItem("recentSearches")).slice(0, 4)
    
    this.getDestinationsData();
    console.log("destinations");
    console.log(this.destinations);
  },

  methods: {
    validateSelection(selection) {
      this.selected = selection;
      this.city = selection.name;
      console.log(selection.name + " has been selected");

      //  alert(selection.name)
    },

    //Method to get restore search
    getCurrentSearch(item){
      this.selected = item.destination
      this.checkedInDate = item.checkinDate
      this.checkedOutDate = item.checkOutDate
      this.noOfAdults = item.adults
      this.noOfChildrens = item.childrens
    },

    getHotels(event) {
      if (this.city == undefined) {
        this.isCitySelected = false;
        return false;
      }

    // Recent Searches implementation
    if(this.recentSearches == null) this.recentSearches = [];
    
     var searches = { destination: this.city, checkinDate: this.checkedInDate, checkOutDate: this.checkedOutDate, adults: this.noOfAdults, childrens: this.noOfChildrens }
    localStorage.setItem("searches", JSON.stringify(searches));

    this.recentSearches.unshift(searches);
    localStorage.setItem("recentSearches", JSON.stringify(this.recentSearches));

    this.$emit("getHotelList", true);
    localStorage.setItem("cityName", this.city);
  
     console.log('Recent Seraches')
    console.log(this.recentSearches)
     
    },

    // Get list of destinations
    getDestinationsData() {
      fetch("destinations.json")
        .then((response) => response.json())
        .then((data) => (this.destinations = data));
    },

     
    getDropdownValues(keyword) {
      console.log(
        "You could refresh options by querying the API with " + keyword
      );
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
  width: 100%;
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

.card {
}
.cardImg {
  border: solid 1px #ccc;
  padding: 20px;
  background: #f9f9f9;
}
.cardImg img {
  max-width: 200px;
}

.rightcolumn .card input {
  width: 100%;
  padding: 10px 15px;
}

.text {
  color: green;
}
.container {
  max-width: 1366px;
  margin: 0px auto;
}
input {
  padding: 8px 12px;
  margin: 0px 3px;
  width: calc(100% - 36px);
}

.d-flex {
  display: flex;
  justify-content: center;
  align-items: end;
}
button {
  height: 34px;
}
label {
  margin-bottom: 4px;
  display: inline-block;
}
form {
}
.adults {
  width: 120px;
}
* {
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
}

/* Float four columns side by side */
.column {
  float: left;
  width: 25%;
  padding: 0 10px;
}

/* Remove extra left and right margins, due to padding */
.row {
  margin: 0 -5px;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Responsive columns */
@media screen and (max-width: 600px) {
  .column {
    width: 100%;
    display: block;
    margin-bottom: 20px;
  }
}

/* Style the counter cards */
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  padding: 16px;
  text-align: center;
  background-color: #f1f1f1;
}
@media screen and (max-width: 767px) {
  body {
    border: solid 0px green;
  }
  label {
    margin-top: 20px;
  }
  .d-flex {
    display: block;
  }
  form {
    margin-top: 10px;
  }
  .adults {
    width: 49.4%;
    display: inline-block;
  }
  button {
    margin-top: 20px;
    margin-left: 3px;
  }
}
</style>
<template>
  <div>
    <div class="row">
      <div class="leftcolumn">
        <div class="card">
          <div class="cardImg">
            <form>
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
                </div>
                <div>
                  <label>Check-In</label>
                  <date-picker v-model="checkedInDate" valueType="format"></date-picker>
                </div>
                <div>
                  <label>Check-Out</label>
                  <date-picker v-model="checkedOutDate" valueType="format"></date-picker>
                </div>
                <div class="adults">
                  <label>Adults</label>
                  <input type="text" />
                </div>
                <div class="adults">
                  <label>Childrens</label>
                  <input type="text" />
                </div>
                <div>
                  <button v-on:click="getHotels()">SEARCH</button>
                </div>
              </div>
            </form>
          </div>
          <br /><br />
          <p>
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley of type
            and scrambled it to make a type specimen book. It has survived not
            only five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged. It was popularised in the 1960s
            with the release of Letraset sheets containing Lorem Ipsum passages,
            and more recently with desktop publishing software like Aldus
            PageMaker including versions of Lorem Ipsum.
          </p>
          <p>
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley of type
            and scrambled it to make a type specimen book. It has survived not
            only five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged. It was popularised in the 1960s
            with the release of Letraset sheets containing Lorem Ipsum passages,
            and more recently with desktop publishing software like Aldus
            PageMaker including versions of Lorem Ipsum.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Dropdown from "vue-simple-search-dropdown";
import DatePicker from 'vue2-datepicker';
import 'vue2-datepicker/index.css';

export default {
  components: {
    Dropdown,
    DatePicker,
  },
  data() {
    return {
      show: false,
      destinations: [
        {
          id: 70,
          name: "Atlanta",
        },
        {
          id: 149,
          name: "Boston",
        },
        {
          id: 5034,
          name: "Boston",
        },
        {
          id: 34501,
          name: "Celebration",
        },
        {
          id: 40418,
          name: "Edgewood",
        },
        {
          id: 39505,
          name: "Gotha",
        },
        {
          id: 21017,
          name: "Haines City",
        },
        {
          id: 10,
          name: "Los Angeles",
        },
        {
          id: 72,
          name: "Miami",
        },
        {
          id: 18421,
          name: "Montverde",
        },
        {
          id: 54,
          name: "New York",
        },
        {
          id: 23767,
          name: "Ocoee",
        },
        {
          id: 32190,
          name: "Orlando area",
        },
        {
          id: 11531,
          name: "Poinciana",
        },
        {
          id: 10772,
          name: "Polk City",
        },
        {
          id: 17969,
          name: "San Francisco Bay",
        },
        {
          id: 17365,
          name: "St. Cloud",
        },
        {
          id: 24263,
          name: "Walt Disney World® Resort",
        },
        {
          id: 277,
          name: "Washington",
        },
        {
          id: 49764,
          name: "Windermere",
        },
        {
          id: 22282,
          name: "Winter Garden",
        },
      ],

      selected: { name: null, id: null },
      checkedInDate: null,
      checkedOutDate: null
    };
  },
  methods: {
    validateSelection(selection) {
      this.selected = selection;
      console.log(selection.name + " has been selected");
    //  alert(selection.name)
    },

    getHotels(){
       // alert('Hi')
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
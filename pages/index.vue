<template>
  <search-form v-if="!isLoadHotel" @getHotelList="getHotels"/>
  <hotel-list @getHotelList="getHotels" v-else/>
</template>

<script>
import HotelList from '../components/hotel-list.vue';
import searchForm from '../components/search-form.vue';
export default {
  components: { searchForm, HotelList },
  
    data() {
    return {
      isLoadHotel: false,

    };
  },

  methods: {
    getHotels(value) {
      this.isLoadHotel = value
    },
  }
  
}
</script>

<template>
<div id="main">
  <h2>Public Holidays</h2>
  <holiday-list :holidays="holidays"></holiday-list>
  <holiday-info v-if="selectedHoliday" :holiday="selectedHoliday"></holiday-info>
  <favourites-list  :favourites="theFavourites"></favourites-list>
  </div>
</template>

<script>
import { eventBus } from "./main.js"
import HolidayList from './components/HolidayList.vue'
import HolidayInfo from './components/HolidayInfo'
import FavouritesList from './components/FavouritesList.vue'


export default {
  name: 'app',
  data() {
    return {
      holidays: [],
      selectedHoliday: null
    }
  },
  components: {
      'holiday-list': HolidayList,
      'holiday-info': HolidayInfo,
      'favourites-list': FavouritesList
    },

    computed: {
       theFavourites: function() {
      return this.holidays.filter(holiday => holiday.isFavourite);
    }
    },

  mounted() {
    fetch('https://date.nager.at/api/v2/PublicHolidays/2017/AT')
    .then(result => result.json())
    .then(theData => {
      theData.forEach(holiday => (holiday.isFavourite = false));
      this.holidays = theData;
    }),

    eventBus.$on('holiday-selected', (holiday) => {
      this.selectedHoliday = holiday
      // console.log('within $on', holiday);

    })

    eventBus.$on('favourite-added', (holiday) => {
      const index = this.holidays.indexOf(holiday);
      this.holidays[index].isFavourite = true;
    })

    eventBus.$on('favourite-removed', (holiday) => {
      const index = this.holidays.indexOf(holiday);
      this.holidays[index].isFavourite = false;
    })
  }


}
</script>

<style>
#main{
  background-color: wheat;
  padding: 10px;
  border-radius: 1em;
}
body{
  background-color: rgb(196, 191, 182);
}

</style>
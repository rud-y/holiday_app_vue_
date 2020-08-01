<template>
<div id="main">
  <h2>Public Holidays</h2>
  <holiday-list :holidays="holidays"></holiday-list>
  <holiday-info v-if="selectedHoliday" :holiday="selectedHoliday"></holiday-info>

  </div>
</template>

<script>
import { eventBus } from "./main.js";
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

  mounted() {
    fetch('https://date.nager.at/api/v2/PublicHolidays/2017/AT')
    .then(result => result.json())
    .then(theData => {
      theData.forEach(holiday => (holiday.isFavourite = false));
      this.holidays = theData;
    }),

    eventBus.$on('holiday-selected', holiday => this.selectedHoliday = holiday);
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
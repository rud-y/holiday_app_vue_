<template>
  <div id="main">

  <h2>Public Holidays List</h2>
  <div class="at"><h4 id="austria">Austria</h4></div>
  <div id="all-info">
  <holiday-list :holidays="holidays"></holiday-list>
  <holiday-info v-if="selectedHoliday" :holiday="selectedHoliday"></holiday-info>
  <favourites-list :favourites="theFavourites"></favourites-list>
  </div>

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
  background-color: silver;
  padding: 20px;
  border-radius: 1em;
  background-color: rgb(196, 191, 182);
  font: 16px fantasy;
}
#all-info{
  display: flex;
}

.at {
 background: url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5MDAgNjAwIj4NCjxwYXRoIGZpbGw9IiNkODFlMDUiIGQ9Im0wLDBoOTAwdjYwMGgtOTAweiIvPg0KPHBhdGggZmlsbD0iI2ZmZiIgZD0ibTAsMjAwaDkwMHYyMDBoLTkwMHoiLz4NCjwvc3ZnPg0K');
 width: 75%;
 height: 100%;
 background-size: 100% 100%;
}
#austria{
  width: 200px;
  color: black;
}

</style>
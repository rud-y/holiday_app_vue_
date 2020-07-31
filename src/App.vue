<template>
<div main>
  <h2>Public Holidays</h2>
  <holiday-list :holidays="holidays"></holiday-list>
  <holiday-info v-if="selectedHoliday" :holiday="selectedHoliday"></holiday-info>
  </div>
</template>

<script>
import { eventBus } from "./main.js";
import HolidayList from './components/HolidayList.vue'
import ListItem from './components/ListItem.vue'
import HolidayInfo from './components/HolidayInfo'

export default {
  data() {
    return {
      holidays: [],
      selectedHoliday: null
    }
  },
  components: {
      'holiday-list': HolidayList,
      'list-item': ListItem,
      'holiday-info': HolidayInfo
    },

  mounted() {
    fetch('https://date.nager.at/api/v2/PublicHolidays/2017/AT')
    .then(result => result.json())
    .then(holidays => this.holidays = holidays)

    eventBus.$on('holiday-selected', holiday => this.selectedHoliday = holiday);
  }


}
</script>

<style>

</style>
<template>
  <div id="favourites-list-item">
      <li>{{holiday.name}}  <button v-on:click="selectHoliday">Display more info</button></li>
      </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
name: 'favourites-list-item',
props: ['holiday'],
methods: {
    selectHoliday: function () {
        eventBus.$emit('holiday-selected', this.holiday);
    }
}
};
</script>

<style>

</style>
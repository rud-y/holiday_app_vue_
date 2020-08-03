<template>
  <div id="favourites-list-item">
      <li>{{holiday.name}}  
          <button class="fav-buttons" v-on:click="removeFromFavourites">Remove</button>
          <button class="fav-buttons" v-on:click="displayInfo">More info</button>
          </li>
      </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
name: 'favourites-list-item',
props: ['holiday'],
methods: {
    removeFromFavourites: function () {
           eventBus.$emit('favourite-removed', this.holiday)
       },
    displayInfo: function () {
            eventBus.$emit('holiday-selected', this.holiday);
    }
}
}


</script>

<style>
.fav-buttons{
    width: 75px;
    padding-left: 4px;
}
</style>
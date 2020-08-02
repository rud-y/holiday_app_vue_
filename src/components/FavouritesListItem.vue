<template>
  <div id="favourites-list-item">
      <li>{{holiday.name}}  
          <button id="remove-btn" v-on:click="removeFromFavourites">Remove</button>
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
#remove-btn{
    width: 60px;
}

</style>
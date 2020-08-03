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
    width: 80px;
    padding-left: 5px;
    background-color: white;
    display: inline-block;
    border-radius: 15px;
}
.fav-buttons:hover {
    background-color:white;
    border: solid 2px red;
}
</style>
<template>
  <div>
        <li id="single-list-item">
            <h4>{{holiday.name}}</h4>
            <button class="list-button" v-on:click="displayInfo">Display info</button>
            <button class="list-button" v-on:click="addToFavourites">Add to favourites</button>
        </li>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name: 'list-item',
    props: ['holiday'],
    methods: {
        displayInfo: function () {
            eventBus.$emit('holiday-selected', this.holiday);
        },

        addToFavourites() {
            eventBus.$emit('favourite-added', this.holiday);
        }
    }
}

</script>

<style>
.list-button{
    width: 125px;
    background-color: white;
    display: block;
    border-radius: 15px;
}
.list-button:hover {
    background-color:white;
    border: solid 2px red;
}
#single-list-item{
    width: 220px;
    height: 110px;
    border: solid 3px whitesmoke;
    border-radius: 15px;
    margin: 5px;
    align-content: center;
    background-color: rgb(126, 55, 55);
}
h4{
    padding: 0;
    text-align: center;
    color: whitesmoke;
    font-size: 16px;
}
</style>
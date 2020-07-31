<template>
  <div>
      <button><li v-on:click="displayInfo">{{holiday.name}}</li></button>

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
        }
    }
}

</script>

<style>
button{
    width: 12em;
}
</style>
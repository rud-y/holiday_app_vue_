<template>
  <div>
      <ul>
      <list-item v-for="(holiday, index) in holidays" 
      :holiday='holiday' :key="index"></list-item>
      </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue'
export default {
    name: 'holiday-list',
    props: ['holidays'],
    components: {
        'list-item': ListItem
    }

}
</script>

<style>
ul {
    list-style: none;
}

</style>
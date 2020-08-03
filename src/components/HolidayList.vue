<template>
  <div id="hol-list">
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
#hol-list{
    padding-left: 20px;
}
ul {
    list-style: none;
}

</style>
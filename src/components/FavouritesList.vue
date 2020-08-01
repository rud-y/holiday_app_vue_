<template>
    <div id="favourites-list">
        <h3>Your favourites</h3>
        <ul>
        <favourite-list-item v-for="(holiday, index) in favourites"
        :holiday="holiday" :key="index"></favourite-list-item>
        </ul>
    </div>
</template>

<script>
import FavouritesListItem from './FavouritesListItem.vue'
export default {
    name: 'favourite-list',
    props: ['favourites'],
    components: {
        'favourite-list-item': FavouritesListItem
    }


}
</script>

<style>

</style>
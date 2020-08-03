<template>
<div id="fav-list-box">
    <div id="favourites-list" v-if="favourites">
        <h3>Your favourites</h3>
        <ul>
            <favourites-list-item v-for="(holiday, index) in favourites"
            :holiday="holiday" :key="index"></favourites-list-item>
        </ul>
    </div>
    </div>
</template>

<script>
import FavouritesListItem from './FavouritesListItem.vue'
export default {
    name: 'favourites-list',
    props: ['favourites'],
    components: {
        'favourites-list-item': FavouritesListItem
    }

}
</script>

<style>
fav-list-box{
    display: flex;
    float: left;
}

</style>
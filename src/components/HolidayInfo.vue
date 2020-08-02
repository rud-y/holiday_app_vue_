<template>
  <div id="single-info">
        <h3 id="info-header">{{holiday.name}}</h3>
        <p>Local name:  <strong>{{holiday.localName}}</strong></p>
        <p>Celebreated on:  <strong>{{holiday.date}}</strong></p>
        <p v-if="holiday.launchYear==null"> Launch year:  <strong>unknown</strong></p>
        <p v-else>Launch year:  <strong>{{holiday.launchYear}}</strong></p>
        
    </div>
</template>

<script>
export default {
    name: 'holiday-info',
    props: ['holiday'],
    methods: {
       
    }

}
</script>

<style>
#single-info{
    padding: 10px;  
}
#info-header{
    border-bottom: solid 2px white;
    width: 200px;
}


</style>
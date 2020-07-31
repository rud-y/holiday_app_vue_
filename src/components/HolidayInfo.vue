<template>
  <div id="info">
      <h3>{{holiday.name}}</h3>
        <p><strong>Local name:  </strong>{{holiday.localName}}</p>
        <p><strong>Celebreated on:  </strong>{{holiday.date}} - {{holiday.fixed}}</p>
        <p><strong>Launch year:  </strong>{{holiday.launchYear}}</p>
    </div>
</template>

<script>
export default {
    props: ['holiday']

}
</script>

<style>


</style>
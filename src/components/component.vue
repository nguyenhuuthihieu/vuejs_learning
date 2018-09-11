<template>
  <div id="components-demo">
    <button-counter></button-counter>
  </div>
</template>

<script>
  import Vue from 'vue';
  new Vue({ el: '#components-demo' })

  Vue.component('button-counter', {
    data: function () {
      return {
        count: 0
      }
    },
    template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
  })
</script>

<style scoped>

</style>

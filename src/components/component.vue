<template>
  <div id="components-demo">
    <button-counter></button-counter>
    <daochuoi></daochuoi>
  </div>
</template>

<script>
  import Vue from 'vue';
  var vm =new Vue({
    el: '#components-demo',
    data() {
      return {
        property: 'Blank'
      }
    },
    computed: {
      reversedMessage: function () {
        return this.massage.split(' ').reverse().join(' ')
      }
    },
    created() {
      console.log('created');
    },
    beforeMount() {
      console.log(`before mount`)
    },
    mounted() {
      console.log('mounted')
    },
    beforeUpdate() {
      console.log('before update')
    },
    updated() {
      console.log('update')
    },
    beforeDestroy() {
      this.property = null
      console.log('before destroy')
      delete this.property
    },
    destroyed() {
      console.log('destroyed')
    },

  });
  vm.$watch('a', function (newVal, oldVal) {//làm gì khi đợi giữa new va old
    console.log(newVal, oldVal)
  });
  Vue.component('button-counter', {
    data: function () {
      return {
        count: 0
      }
    },
    template: '<button v-on:click="count++">You clicked me {{ count }} times. </button> '
  });
  Vue.component('daochuoi',{
    data:function () {
      return{
        massage:'abc'
      }
    },
    computed: {
      reversedMessage: function () {
        return this.massage;
      }
    },
    template:'<p>Thông điệp bị đảo ngược bằng tính toán (computed): "{{ reversedMessage }}"</p>'
  })
</script>

<style scoped>

</style>

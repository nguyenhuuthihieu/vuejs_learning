<template>
    <div>component2</div>
</template>

<script>
    export default {
      name: "component2",
      props: {
        value: {
          type: String,
          default: '',
        }
      },
      data:{
        massage:'component2',
      }
    }
</script>

<style scoped>

</style>

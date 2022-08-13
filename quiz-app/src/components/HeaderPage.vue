<template>
  <div class="header">
    <b-nav tabs>
        <b-nav-item disabled>Fancy Quiz App</b-nav-item>
        <b-nav-item disabled>Counter: {{numCorrect}}/{{numTotal}}</b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
    name: 'HeaderPage',

    props: [
      'numCorrect', 
      'numTotal'
    ]
    

}
</script>

<style scoped>

.header{
    width: 80%;
}

</style>
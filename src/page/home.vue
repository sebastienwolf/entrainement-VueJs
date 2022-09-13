<template>
  <div class="home">
<RestaurantRow/>

  </div>
</template>

<script>
    // import
    import BDD from '../BDD.js'
    // components
    import RestaurantRow from '../components/RestaurantRow.vue'
export default {
name:'Home',
components: {
    RestaurantRow
},
setup(){
  console.log(BDD);
  class Restaurant {
    constructor(name, note, image, drive_time){
      this.name = name
      this.note = note
      this.image = image
      this.drive_time = drive_time

    }
  }

  var resto = new Restaurant('restaura,t lechat',4.5, 'img', '45mn')
console.log(resto);
}

}
</script>

<style>

</style>
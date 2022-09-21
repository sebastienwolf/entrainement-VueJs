<template>
  <div class="home">
    <div class="header">
      <img src="https://d3i4yxtzktqr9n.cloudfront.net/web-eats-v2/ee037401cb5d31b23cf780808ee4ec1f.svg" alt="" srcset="">
      <input v-model="user_search_restaurant" type="text" placeholder="De quoi avez vous envie ?">
    </div>
    <div class="bannier"></div>
<RestaurantRow v-for="(data, i) in data_restaurant" :key="i" :three_restaurant ="data"/>

  </div>
</template>

<script>
    // import
    import BDD from '../BDD.js'
    import { onMounted, ref, watch } from 'vue'
    // components
    import RestaurantRow from '../components/RestaurantRow.vue'
export default {
name:'Home',
components: {
    RestaurantRow
},
setup(){

  class Restaurant {
    constructor(name, note, image, drive_time){
      this.name = name
      this.note = note
      this.image = image
      this.drive_time = drive_time
    }
  }

let data_restaurant = ref([])
let all_restaurant=[]

const makeDataRestaurant = () =>{
  let three_restaurant = [];
  for ( const restaurant of BDD.data){
    const new_restaurant = new Restaurant(restaurant.name, restaurant.note, restaurant.image,
    restaurant.drive_time)
    //make all restaurant array
    all_restaurant.push(new_restaurant)

    if(three_restaurant.length === 2){
      three_restaurant.push(new_restaurant)
      data_restaurant.value.push(three_restaurant)
      three_restaurant =[]

    }else{
      three_restaurant.push(new_restaurant)
    }
  }
} 
//user search restaurant
let user_search_restaurant = ref('')

watch(user_search_restaurant, (new_value, old_value)=>{
  console.log(new_value);
  console.log(old_value);
  console.log(all_restaurant);
  let regex = RegExp(new_value)
  let test_array= all_restaurant.filter(restaurant => regex.test(restaurant.name))
  console.log(test_array);
} )

onMounted(makeDataRestaurant);
//return
return {
  data_restaurant,
  user_search_restaurant,
}
}
}
</script>

<style lang="scss">
.home{
  .header{
   height: 120px;
   width: 100%;
   display: flex;
  align-items: center;
  justify-content: space-between;
   img{
    width: 200px;
  }
  input{
    background-color: #f6f6f6;
    border: none;
    height: 60px;
    width: 400px;
    outline: none;
    padding-left: 20px;

  }

  }
  .bannier{
    height: 200px;
    width: 100%;
    background-image: url(https://www.ubereats.com/restaurant/_static/7b308f7cbbf8e335ceda0447a8bd7c63.png);
    background-size: cover;
    background-position: center center;
  }
}
</style>
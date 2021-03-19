<template>
<div class="horizontal">
  <div class="side-list" v-for="ingredient of ingredientsBaked" :key="ingredient">
  {{ ingredient }}
  </div>
</div>
<button v-on:click=bakeThatCake()>BAKE THAT CAKE</button>
<p id="result"></p>
</template>

<script>

export default {
  name: 'Baked',
  props: {
    ingredientsBaked: {
      type: Array,
      required: true,
    }
  },
  setup(props){
    function bakeThatCake(){
      if (props.ingredientsBaked.includes("flour")){
        if (props.ingredientsBaked.includes("milk")){
          if (props.ingredientsBaked.includes("eggs")){
            if (props.ingredientsBaked.includes("butter")){
              if (props.ingredientsBaked.includes("sugar")){
                document.getElementById("result").innerHTML = "PANCAKES"
              }
              else{ //flour, milk, eggs, butter
                document.getElementById("result").innerHTML = "Crepes!"
              }
            }else{
              if (props.ingredientsBaked.includes("sugar")){ //flour, milk, eggs, sugar
                document.getElementById("result").innerHTML = "Brioche! Or... maybe Angel Food cake?"
              }else{ //flour, milk, eggs...
                document.getElementById("result").innerHTML = "Seems like you might need to add butter..."
              }
            }
          }else{
            if (props.ingredientsBaked.includes("butter")){ //flour, milk, butter...
              if (props.ingredientsBaked.includes("sugar")){ //flour, milk, butter, sugar
                document.getElementById("result").innerHTML = "Vegan pancakes?"
              }else{ //no sugar, just flour milk butter
                document.getElementById("result").innerHTML = "Biscuits!"
            }
          } document.getElementById("result").innerHTML = "Ooh, milk bread!" //MILK AND FLOUR
        }

          }else{
          if (props.ingredientsBaked.includes("eggs")){ //flour, eggs...
            if (props.ingredientsBaked.includes("butter")){ //flour, eggs, butter
              if (props.ingredientsBaked.includes("sugar")){ //flour, eggs, butter, sugar
                document.getElementById("result").innerHTML = "I think it would help if you added milk!"
              }else{
                document.getElementById("result").innerHTML = "I think it would help if you added milk!"
              }
            }
            document.getElementById("result").innerHTML = "I think it would help if you added milk!" //flour and eggs
          }else{
            document.getElementById("result").innerHTML = "Well.. you can make bread... if you have water."
          }
        }
      }else{
        if (props.ingredientsBaked.includes("milk")){
          if (props.ingredientsBaked.includes("eggs")){
            document.getElementById("result").innerHTML = "...scrambled eggs!"  //no flour, just milk and eggs
          }else{
            if (props.ingredientsBaked.length < 2){ //if there's ONLY milk
              document.getElementById("result").innerHTML = "...drink the milk, I guess"
            }
          }
        }else{
          document.getElementById("result").innerHTML = "Add more ingredients!"
        }
      }
    }
      return {
        bakeThatCake
      };
    }
}
</script>


<style>
.horizontal{
  display: flex;
  flex-direction: row;
  margin-left: auto;
  margin-right: auto;
  place-content: center;
}
.side-list{
  padding: 10px;
}
</style>

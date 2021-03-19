<template>
<h1>Let's bake!</h1>
<p>Select the ingredients that you want to mix together. Then, click "bake" and see what it makes!</p>
  <Ingredient fieldId="eggs" v-model:ingredients="ingredients"/>
  <Ingredient fieldId="milk" v-model:ingredients="ingredients"/>
  <Ingredient fieldId="flour" v-model:ingredients="ingredients"/>
  <Ingredient fieldId="butter" v-model:ingredients="ingredients"/>
  <Ingredient fieldId="sugar" v-model:ingredients="ingredients"/>
  <Baked v-model:ingredientsBaked="ingredients"/>
</template>

<script>
import Ingredient from './components/Ingredient.vue';
import Baked from './components/Baked.vue';
import { ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const ingredients = ref ([])
    return {
      ingredients
    }
  },
  components: {
    Ingredient,
    Baked,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

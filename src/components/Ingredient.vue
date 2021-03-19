<template>
  <div class="Bakery">
      <input type="checkbox"
        :id="fieldId"
        @input="check()"/>  <label
        :for="fieldId"
        class="mr-2 hidden"
        v-bind="$attrs"
        >
        {{ fieldId }}

        <i class="fa mr-2"
        :class="{
          'fa-egg': ingredients.includes(fieldId),
          'fas fa-times': !ingredients.includes(fieldId),
        }"
        ></i>
      </label>
  </div>
</template>

<script>
import { computed } from "vue";

export default {
    emits: ["update:ingredients"],
    props: {
      fieldId: {
        type: String,
        required: true,
      },
      ingredients: {
        type: Array,
        required: true,
      },
    },

    setup(props, context) {
      const ingredientIn = computed(() => props.ingredients.includes(props.fieldId));

      function check() {
        // copy the ingredients
        let updatedIngredients = [...props.ingredients];
        // remove ingredient if checked, else add ingredient
        if (this.ingredientIn) {
          updatedIngredients.splice(updatedIngredients.indexOf(props.fieldId), 1);
        } else {
          updatedIngredients.push(props.fieldId);
        }
        // emit the updated ingredients
        context.emit("update:ingredients", updatedIngredients);
      }

      return {
        check,
        ingredientIn,
      };
    },

  name: 'Ingredient'
}
</script>;
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

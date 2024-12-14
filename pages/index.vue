<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>

      <div class="text-center">
        <!-- <logo />
        <vuetify-logo /> -->
      </div>

      <v-row class="row d-flex" no-gutters>
        <v-col class="col-4">
          <v-card class="custom-card">

            <div>
              <p class="white--text">Indulge in guilt-free <br> healthy meals</p>
              <!-- <v-btn class="white--text" color="#45B69C" :to="{ path: '/recipe' }">Find more recipes</v-btn> -->
              <v-btn class="custom-btn" :to="{ path: '/recipe' }" color="white" dark outlined>
                Find more recipes
              </v-btn>
            </div>

          </v-card>
        </v-col>

        <v-col class="col-8">
          <v-img height="400" src="/lasagna.jpg"></v-img>
        </v-col>
      </v-row>

      <v-row class="row">
        <v-form v-model="valid" class="col-8">
          <v-container>
            <v-row>

              <div class="mt-5">
                <strong>
                  <p>Easily calculate the nutritional value of your favorite recipes and meals with just a few clicks</p>
                </strong>
              </div>

              <v-col cols="12">
                <v-text-field v-model="recipe_name" :rules="nameRules" :counter="10" label="Recipe Name" required
                  hide-details outlined></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-textarea v-model="recipe_ingredients" :rules="ingredientsRules" :counter="200"
                  label="Recipe Ingredients" required outlined></v-textarea>
              </v-col>

              <v-col cols="6">
                <v-text-field v-model="servings" :rules="servingsRules" label="No. of Servings" hide-details required
                  outlined></v-text-field>
              </v-col>

              <v-col cols="6">
                <v-text-field v-model="serving_size" :rules="servingSizeRules" label="Serving Size" hide-details required
                  outlined></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-btn class="white--text" @click="calculateRecipe" :disabled="!valid" color="#024A42">Calculate
                  Recipe</v-btn>
              </v-col>

            </v-row>
          </v-container>
        </v-form>

        <div class="advertisement-container row col-4">
          <div class="mt-5">
            <strong>
              <p>Easily calculate the nutritional value of your favorite recipes and meals with just a few clicks</p>
            </strong>
            <v-card class="row col-12" color="grey">
              <div>
                <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
              </div>
            </v-card>
          </div>
        </div>
      </v-row>

      <div>
        <strong>Explore more recipes</strong>
        <p>
          <br>
          Browse through a vast database of delicious recipes, each accompanied by a nutrition breakdown including calorie
          count, macro- and micronutrient information, and more. Customize the serving size to fit your needs and see the
          nutritional information based on the exact amount you plan to eat. With a constantly updating database of
          recipes, the possibilities are endless, so start exploring today and take control of your nutritional choices!
        </p>
      </div>

      <v-row class="mt-5">
        <!-- <v-card class="col-6 d-flex"><img src="/lasagna.jpg" height="250" width="300">
          <div class="ml-5">

            <strong>Lasagna</strong>
            <p>1 Serving = 100cal</p>

            <div class="d-flex">
              <div>
                <div>4%</div>
                <div>13.9g</div>
                <div>Carbs</div>
              </div>

              <div class="pl-5">
                <div>4%</div>
                <div>13.9g</div>
                <div>Carbs</div>
              </div>

              <div class="pl-5">
                <div>4%</div>
                <div>13.9g</div>
                <div>Carbs</div>
              </div>
            </div>

          </div>
        </v-card> -->

        <v-card class="col-6 d-flex" v-for="recipes in  recipe " :key="recipes.id">
          <img :src="recipes.image_url" height="250" width="300">
          <div class="ml-5">

            <strong>{{ recipes.recipe_name }}</strong>
            <p>1 serving = 100cal</p>

            <div class="d-flex">
              <div>
                <div>4%</div>
                <div>13.9g</div>
                <div>Carbs</div>
              </div>

              <div class="pl-5">
                <div>4%</div>
                <div>13.9g</div>
                <div>Carbs</div>
              </div>

              <div class="pl-5">
                <div>4%</div>
                <div>13.9g</div>
                <div>Carbs</div>
              </div>
            </div>

          </div>
        </v-card>
      </v-row>
      <br>
    </v-flex>
  </v-layout>
</template>

<style scoped>
.custom-card {
  background-color: #024A42;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.custom-card>div {
  text-align: center;
}

/* Ensure the advertisement text is above the card */
.v-card {
  position: relative;
  z-index: 0;
}

.custom-btn {
  color: white !important;
  background-color: #45B69C;
  border-color: #45B69C !important;
  transition: background-color 0.3s ease;
  /* Add smooth transition effect */

}

.custom-btn:hover {
  background-color: white !important;
  border-color: white !important;
  color: #024A42 !important;
}
</style>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {

  components: {
    Logo,
    VuetifyLogo,

  },

  data() {
    return {
      valid: false,
      recipe_name: '',
      recipe_ingredients: '',
      servings: '',
      serving_size: '',
      recipe: [],
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      ingredientsRules: [
        v => !!v || 'Ingredients are required',
        v => (v && v.length <= 200) || 'Ingredients must be less than 200 characters',
      ],
      servingsRules: [
        v => !!v || 'No. of Servings is required',
      ],
      servingSizeRules: [
        v => !!v || 'Serving Size is required',
      ],
    };
  },

  methods: {
    calculateRecipe() {
      // Add your logic for calculating the recipe here
      // You can use the values from data properties (e.g., this.recipe_name, this.recipe_ingredients, etc.)
      // For example, you might want to perform some calculations based on the input values
      console.log('Recipe calculated!');
    },

    // sapag display ni nga part
    async fetchRecipeData() {
      try {
        const response = await this.$axios.get('api/display');
        this.recipe = response.data;
      } catch (error) {
        console.error('Error:', error);
      }
    },
  },

  //sapag fectch ni sa display ni nga part
  async mounted() {
    await this.fetchRecipeData();
  },
  
};

</script> 
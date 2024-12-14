<template>
    <div>
        <a href="/recipe" class="custom-recipe">
            <span class="text-decoration-underline">
                <strong>
                    Recipe
                </strong>
            </span>
        </a>
        <span>>> Favorites >> Nutrition Facts</span>

        <div class="mt-5">
            <strong>{{ recipe.recipe_name }}</strong>
        </div>

        <div align="center">
            <v-col class="row col-12 mt-5" style="height: 500px; overflow: hidden;">
                <img :src="recipe.image_url" style="object-fit: cover; width: 100%; height: 100%; border-radius: 30px;">
            </v-col>
        </div>

        <br>
        <br>

        <div>
            <span>
                {{ recipe.recipe_description }}
            </span>
        </div>

        <br>
        <br>

        <div>
            <v-row class="row">
                <v-col class="col-6">
                    <v-card height="500">
                        <br>
                        <strong class="ml-5">ingredient</strong>
                        <div class="ml-5 pl-5 mt-5">
                            <div>
                                <span>•</span><span> Ingredients:</span>
                            </div>

                            <div>
                                <span>•</span><span> 9 lasagna noodles</span>
                            </div>

                            <div>
                                <span>•</span><span> 1 lb ground beef or Italian sausage</span>
                            </div>

                            <div>
                                <span>•</span><span> 1 large onion, chopped</span>
                            </div>

                            <div>
                                <span>•</span><span> 3 cloves of garlic, minced</span>
                            </div>

                            <div>
                                <span>•</span><span> 1 (28 oz) can of crushed tomatoes</span>
                            </div>

                            <div>
                                <span>•</span><span> 2 tablespoons tomato paste</span>
                            </div>

                            <div>
                                <span>•</span><span> 1 teaspoon dried basil</span>
                            </div>

                            <div>
                                <span>•</span><span> 1 teaspoon dried oregano</span>
                            </div>

                            <div>
                                <span>•</span><span> Salt and pepper, to taste</span>
                            </div>

                            <div>
                                <span>•</span><span> 15 oz ricotta cheese</span>
                            </div>

                            <div>
                                <span>•</span><span> 1 large egg</span>
                            </div>

                            <div>
                                <span>•</span><span> 2 cups grated mozzarella cheese</span>
                            </div>

                            <div>
                                <span>•</span><span> 1/2 cup grated Parmesan cheese</span>
                            </div>
                        </div>

                    </v-card>
                </v-col>

                <v-col class="col-6">
                    <v-card height="500">
                        <br>
                        <strong class="ml-5">Nutrition Facts (per serving, based on 8 servings):</strong>

                        <div class="ml-5 pl-5 mt-5">
                            <div>
                                <span>•</span><span> Calories: 476</span>
                            </div>

                            <div>
                                <span>•</span><span> Total Fat: 28g</span>
                            </div>

                            <div>
                                <span>•</span><span> Saturated Fat: 14g</span>
                            </div>

                            <div>
                                <span>•</span><span> Cholesterol: 109mg</span>
                            </div>

                            <div>
                                <span>•</span><span> Sodium: 899mg</span>
                            </div>

                            <div>
                                <span>•</span><span> Total Carbohydrates: 31g</span>
                            </div>

                            <div>
                                <span>•</span><span> Dietary Fiber: 3g</span>
                            </div>

                            <div>
                                <span>•</span><span> Sugars: 8g</span>
                            </div>

                            <div>
                                <span>•</span><span> Protein: 27g</span>
                            </div>
                        </div>

                    </v-card>
                </v-col>
            </v-row>
        </div>

        <br>
        <br>

        <div>
            <span>
                <strong>
                    Health and Benefits
                </strong>
            </span>

            <div>
                <span>Lasagna can offer several health benefits including a good source of protein from ground beef or
                    sausage, whole grains from whole-grain pasta providing fiber for digestion and weight management,
                    vegetables for increased vitamin, mineral and antioxidant content, calcium from cheese for strong bones
                    and can also serve as comfort food to boost mood and reduce stress. However, it's important to consider
                    portion control and the use of lean meat, low-fat cheese, and plenty of vegetables to maintain a
                    balanced and healthy diet.
                </span>
            </div>
        </div>

    </div>
</template>

<style lang="scss" scoped>
.custom-recipe {
    color: #45B69C;
    /* Set the default text color */
    transition: color 0.3s ease;
    /* Add smooth transition effect */
    text-decoration: none;
    /* Remove default underline style */
}

.custom-recipe:hover {
    color: black;
    /* Set the hover text color to red */
}
</style>

<script>
export default {
    data() {
        return {
            recipe: {},
        };
    },

    methods: {

        // sapag display ni nga part
        async fetchRecipeData() {
            const recipeId = this.$route.query.id;
                    
            try {
                const response = await this.$axios.get(`api/show/${recipeId}`);
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
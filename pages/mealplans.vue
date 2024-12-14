<template>
    <div>
        <div class="text-decoration-underline mt-5">
            <strong>Recipe </strong>
        </div>

        <div class="row mt-5">
            <div>
                <v-btn class="custom-btn" :to="{ path: '/recipe' }" color="white" dark outlined>
                    Favorites
                </v-btn>
                <v-btn class="white--text" :to="{ path: '/mealplans' }" color="#45B69C">Meal Plans</v-btn>
            </div>
        </div>

        <div class="row">
            <v-col class="col-4">
                <v-card color="#21D19F0D">
                    <div class="ml-5">
                        <br>
                        <div><strong>Meal Planing</strong></div>
                        <br>
                        <div>Day 1</div>
                        <br>
                        <div>Day 2</div>
                        <br>
                        <div>Day 3</div>
                        <br>
                        <div>Day 4</div>
                        <br>
                        <div>Day 5</div>
                        <br>
                        <div>Day 6</div>
                        <br>
                        <div>Day 7</div>
                        <br>
                    </div>
                </v-card>
            </v-col>

            <v-col class="col-8">
                <v-card color="#21D19F0D">
                    <div class="ml-5">
                        <br>
                        <div><strong>Meal Planing</strong></div>
                        <br>
                        <div>Day 1
                            <div>
                                <small>Breakfast: Avocado Toast - 2 slices of whole-grain toast, 1 ripe avocado, sliced, 1
                                    tomato,diced, 1 tablespoon of lemon juice, salt and pepper to taste.
                                    <div class="mt-2">
                                        Lunch: Grilled Chicken Salad - 4 ounces of grilled chicken breast, mixed
                                        greens,cherry
                                        tomatoes, cucumber, red onion, 1 tablespoon of balsamic vinaigrette.
                                    </div>
                                    <div class="mt-2">
                                        Dinner: Quinoa and Black Bean Stuffed Bell Peppers - 4 large bell peppers, 1 cup of
                                        cooked quinoa, 1 can of black beans, 1 diced tomato, 1/2 diced onion, 1 clove of
                                        minced
                                        garlic, 1/2 teaspoon of chili powder, salt and pepper to taste.
                                    </div>
                                </small>
                            </div>
                        </div>
                        <br>
                        <div>Day 2
                            <div>
                                <small>Breakfast: Greek Yogurt with Berries and Nuts - 1 cup of Greek yogurt, 1/2 cup of
                                    mixed berries, 2 tablespoons of chopped nuts.
                                    <div class="mt-2">
                                        Lunch: Turkey and Veggie Wrap - 1 whole-grain wrap, 4 ounces of sliced turkey,
                                        lettuce,
                                        tomato, cucumber, 1 tablespoon of hummus.
                                    </div>
                                    <div class="mt-2">
                                        Dinner: Baked Sweet Potato and Black Bean Tacos - 4 corn tortillas, 1 large sweet
                                        potato, 1 can of black beans, 1 diced onion, 1 clove of minced garlic, 1 teaspoon of
                                        chili powder, salt and pepper to taste, 1/2 cup of shredded cheese, and salsa for
                                        serving.
                                    </div>
                                </small>
                            </div>
                        </div>
                        <br>
                        <div>Day 3
                            <div>
                                <small>Breakfast: Smoothie Bowl - 1 cup of frozen berries, 1 banana, 1/2 cup of Greek
                                    yogurt, 1/2 cup of almond milk, 1 tablespoon of honey.
                                    <div class="mt-2">
                                        Lunch: Tuna Salad - 4 ounces of canned tuna, mixed greens, cherry tomatoes,
                                        cucumber,red onion, 1 tablespoon of lemon juice, salt and pepper to taste.
                                    </div>
                                    <div class="mt-2">
                                        Dinner: Stuffed Zucchini Boats - 4 medium zucchini, 1 pound of ground turkey, 1
                                        diced onion, 1 clove of minced garlic, 1 can of diced tomatoes, 1/2 cup of cooked
                                        quinoa,
                                        salt and pepper to taste, 1/2 cup of shredded cheese.
                                    </div>
                                </small>
                            </div>
                        </div>
                        <br>
                        <div>Day 4
                            <div>
                                <small>Breakfast: Peanut Butter Banana Oatmeal - 1/2 cup of rolled oats, 1 banana, 1
                                    tablespoon of peanut butter, 1/2 cup of almond milk.
                                    <div class="mt-2">
                                        Lunch: Veggie and Hummus Wrap - 1 whole-grain wrap, mixed greens, cherry tomatoes,
                                        cucumber, red onion, 1 tablespoon of hummus.
                                    </div>
                                    <div class="mt-2">
                                        Dinner: Baked Salmon and Broccoli - 4 ounces of salmon, 1 head of broccoli, 1
                                        tablespoon of olive oil, lemon juice, salt and pepper to taste.
                                    </div>
                                </small>
                            </div>
                        </div>
                        <br>
                        <div>Day 5
                            <div>
                                <small>Breakfast: Scrambled Eggs and Whole-Grain Toast - 2 eggs, 1 slice of whole-grain
                                    toast, salt and pepper to taste.
                                    <div class="mt-2">
                                        Lunch: Chicken and Quinoa Bowl - 4 ounces of grilled chicken breast, 1 cup of cooked
                                        quinoa, mixed greens, cherry tomatoes, cucumber, red onion, 1 tablespoon of balsamic
                                        vinaigrette.
                                    </div>
                                    <div class="mt-2">
                                        Dinner: Spaghetti Squash and Meat Sauce - 1 medium spaghetti squash, 1 pound of
                                        ground
                                        beef, 1 diced onion, 1 clove of minced garlic, 1 can of diced tomatoes, salt and
                                        pepper
                                        to taste.
                                    </div>
                                </small>
                            </div>
                        </div>
                        <br>
                        <div>Day 6
                            <div>
                                <small>Breakfast: Oatmeal with Mixed Berries and Almonds - 1 cup old-fashioned oats, 1 cup
                                    mixed berries (strawberries, blueberries, raspberries), 1/4 cup almonds, 1 cup almond
                                    milk.
                                    <div class="mt-2">
                                        Lunch: Grilled Chicken Salad - 4 oz grilled chicken breast, 2 cups mixed greens, 1/2
                                        cup
                                        cherry tomatoes, 1/4 cup cucumber, 1/4 cup red onion, 1 tbsp balsamic vinegar, 1
                                        tbsp
                                        extra-virgin olive oil.
                                    </div>
                                    <div class="mt-2">
                                        Dinner: Baked Salmon with Roasted Broccoli - 4 oz salmon fillet, 1 head of broccoli,
                                        1
                                        tbsp olive oil, Salt and pepper to taste.
                                    </div>
                                </small>
                            </div>
                        </div>
                        <br>
                        <div>Day 7
                            <div>
                                <small>Breakfast: Veggie Scrambled Eggs - 2 eggs, 1/2 cup cherry tomatoes, 1/4 cup red bell
                                    pepper, 1/4 cup mushrooms, Salt and pepper to taste
                                    <div class="mt-2">
                                        Lunch: Turkey Wrap with Avocado - 2 slices of whole grain wrap, 4 oz sliced turkey,
                                        1/4
                                        avocado, 1/4 cup red bell pepper, 1/4 cup lettuce.
                                    </div>
                                    <div class="mt-2">
                                        Dinner: Slow Cooker Chicken Tacos - 4 oz shredded chicken, 2 corn tortillas, 1/4 cup
                                        salsa, 1/4 cup shredded lettuce, 1 tbsp sour cream".
                                    </div>
                                </small>
                            </div>
                        </div>
                        <br>
                    </div>

                </v-card>
            </v-col>
        </div>
    </div>
</template>

<style scoped>
.custom-btn {
    color: #45B69C !important;
    border-color: #45B69C !important;
    transition: background-color 0.3s ease;
    /* Add smooth transition effect */

}

.custom-btn:hover {
    background-color: #024A42 !important;
    color: white !important;
}
</style>
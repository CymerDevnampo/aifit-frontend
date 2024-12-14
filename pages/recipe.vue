<template>
    <div>
        <div class="text-decoration-underline mt-5">
            <strong>Recipe </strong>
        </div>

        <div class="row mt-5">
            <div>
                <v-btn class="white--text" to="/recipe" color="#45B69C">Favorites</v-btn>
                <v-btn class="custom-btn" to="/mealplans" color="white" dark outlined>
                    Meal plans
                </v-btn>
            </div>
        </div>

        <div class="row">

            <v-row>

                <v-col cols="12" md="4" v-for="recipes in  recipe " :key="recipes.id" align="center">
                    <v-card class="mt-5" max-width="350" style="border-radius: 30px;">

                        <router-link :to="{ name: 'recipe-preview', query: { id: recipes.id } }">
                            <v-img :src="recipes.image_url" height="200px" cover
                                style="border-top-left-radius: 30px; border-top-right-radius: 30px;"></v-img>
                        </router-link>

                        <v-card-title>{{ recipes.recipe_name }}</v-card-title>
                        <v-card-subtitle>{{ truncateText(recipes.recipe_description, 100) }}</v-card-subtitle>
                    </v-card>
                </v-col>

            </v-row>

        </div>

        <v-row justify="center">
            <v-col cols="auto">
                <v-btn class="white--text" color="#024A42" size="x-large" @click="openModal">Add Recipe</v-btn>
                <v-dialog v-model="modal" max-width="600">
                    <v-card>
                        <!-- Your modal content goes here -->
                        <v-card-title>Add Recipe</v-card-title>
                        <v-card-text>
                            <!-- Your form or other content goes here -->
                            <v-form @submit.prevent="submitForm" enctype="multipart/form-data">
                                <v-file-input label="File Input" v-model="fileInput"></v-file-input>
                                <v-text-field label="Recipe Name" v-model="recipeName"></v-text-field>
                                <v-text-field label="Recipe Description" v-model="recipeDescription"></v-text-field>
                                <v-btn type="submit" color="success">Submit</v-btn>
                            </v-form>
                        </v-card-text>

                        <v-card-actions>
                            <v-btn @click="closeModal" color="error">Close</v-btn>
                        </v-card-actions>
                    </v-card>
                </v-dialog>
            </v-col>
        </v-row>

        <div class="mt-5">
            <p>
                AiFIT - the revolutionary recipe nutrition calculator! Our app makes it simple for you to calculate the
                nutrition value of your favorite recipes and make informed food choices.
                With AiFIT, you can easily input the ingredients of your recipe and receive a comprehensive report on the
                calorie count, macronutrient ratio, and more. Whether you're a fitness enthusiast, looking to manage a
                specific dietary need, or simply want to make healthier food choices, AiFIT is the perfect tool for you.
                Our user-friendly interface and accurate results make it easy to track your daily food intake and stay on
                track with your health and fitness goals. So why wait? Sign up today and start using AiFIT to make every
                meal a healthy and nutritious one!
            </p>
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

<script>
import Swal from 'sweetalert2';

export default {
    data() {
        return {
            modal: false,
            fileInput: null,
            recipeName: '',
            recipeDescription: '',
            recipe: [],
        };
    },

    methods: {
        openModal() {
            this.modal = true;
        },
        closeModal() {
            this.modal = false;
        },
        truncateText(text, maxLength) {
            if (text.length > maxLength) {
                return text.substring(0, maxLength) + '...';
            }
            return text;
        },

        //sapag submit to the database
        async submitForm() {
            try {
                const formData = new FormData();
                formData.append('recipe_name', this.recipeName);
                formData.append('recipe_description', this.recipeDescription);

                // Use a meaningful name for the file input field (e.g., 'recipe_image')
                formData.append('image', this.fileInput);

                // Make a POST request to the Laravel backend
                const response = await this.$axios.post('api/recipes', formData);

                console.log(response.data); // Response from the backend
                Swal.fire({
                    title: 'Success!',
                    text: 'Recipe Added successfully.',
                    icon: 'success',
                    timer: 2000,
                });

                // Close the modal after form submission
                this.closeModal();
                this.fetchRecipeData();
                // setTimeout(() => {
                //     // Reload the page to reflect the added dish
                //     location.reload(true); // true forces a reload from the server, bypassing the cache
                // }, 2000);

            } catch (error) {
                console.error('Error:', error);
                Swal.fire({
                    title: "Error",
                    text: "Failed to add the recipe.",
                    icon: "error"
                });
            }
        },

        // sapag display ni nga part
        async fetchRecipeData() {
            try {
                const response = await this.$axios.get('api/recipes');
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

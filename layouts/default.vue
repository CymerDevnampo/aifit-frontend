<template>
  <v-app dark>
    <v-app-bar app class="custom-header" :clipped-left="clipped" fixed>

      <!-- LEFT BURGER -->
      <v-app-bar-nav-icon v-if="$vuetify.breakpoint.xsOnly" @click.stop="drawer = !drawer" />

      <a href="/" class="white--text" style="text-decoration: none;">
        <strong>
          <v-toolbar-title v-text="title" :class="{ 'text-center': isMobile }" />
        </strong>
      </a>

      <v-spacer />

      <!-- Navigation Links -->
      <div class="nav d-flex justify-end bg-surface-variant" v-if="displayLinks">

        <a href="/" @click="navigate('/')">Home</a>
        <a href="/recipe" @click="navigate('/recipe')">Recipes</a>
        <a href="#" @click="navigate('#')">Community</a>
        <a href="#" @click="navigate('#')">About us</a>
      </div>
    </v-app-bar>

    <!-- NAVIGATION DRAWER -->
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" :clipped="clipped" fixed app>
      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- CONTENT AREA -->
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <!-- RIGHT DRAWER -->
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>mdi-repeat</v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- FOOTER -->
    <v-footer class="d-flex flex-column">
      <div class="bg-teal d-flex w-100 align-center px-4">
        <strong>Get connected with us on social networks!</strong>
        <v-spacer></v-spacer>
      </div>
      <div>
          <a href="https://www.facebook.com/cymerjacob.denampo.9" target="_blank" class="mx-4" size="small" variant="plain"><v-icon color="primary">mdi-facebook</v-icon></a>
          <a href="https://github.com/cymerdenampo" target="_blank" class="mx-4" size="small" variant="plain"><v-icon color="black">mdi-github</v-icon></a>
          <a href="https://www.linkedin.com/in/cymer-denampo-384561280" target="_blank" class="mx-4" size="small" variant="plain"><v-icon color="primary">mdi-linkedin</v-icon></a>
        </div>
      <div class="px-4 py-2 bg-black text-center w-100">
        {{ new Date().getFullYear() }} — <strong>AiFiT - Cymer</strong>
      </div>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
      items: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-food',
          title: 'Recipe',
          to: '/recipe'
        },
        {
          icon: 'mdi-account-group',
          title: 'Community',
          to: '/community'
        },
        {
          icon: 'mdi-information',
          title: 'About us',
          to: '/about'
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'AiFIT',
    };
  },
  computed: {
    isMobile() {
      return this.$vuetify.breakpoint.smAndDown;
    },
    displayLinks() {
      return this.$vuetify.breakpoint.mdAndUp && !this.drawer;
    },
  },
  watch: {
    '$vuetify.breakpoint.mdAndUp': function (isDesktop) {
      // Close the drawer when transitioning from mobile to web view
      if (isDesktop) {
        this.drawer = false;
      }
    },
  },
  methods: {
    navigate(to) {
      this.$router.push(to);
      this.drawer = false; // Close the drawer after navigating
    },
  },
};
</script>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@mdi/font/css/materialdesignicons.min.css">

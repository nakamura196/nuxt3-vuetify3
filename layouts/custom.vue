<template>
  <v-app>
      <v-app-bar id="bar" dark app color="success" flat>
      <v-toolbar-title>
        <nuxt-link
          :to="
            {
              name: 'index',
            }
          "
          style="color: inherit; text-decoration: inherit"
        >
          {{ "Nuxt 3 x Vuetify 3" }}
        </nuxt-link>
      </v-toolbar-title>
      </v-app-bar>
    <v-main>
      <v-container>
        <slot />
      </v-container>
    </v-main>
    <v-footer
    class="bg-grey-lighten-1 mt-10"
  >
    <v-row
      justify="center"
      no-gutters
    >
      <v-col
        class="text-center text-white my-4"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Satoru Nakamura</strong>
      </v-col>
    </v-row>
  </v-footer>
  </v-app>
</template>
<template>
  <v-app>
    <v-app-bar id="bar" dark app color="success" flat>
      <v-app-bar-nav-icon
        class="mr-2"
        variant="text"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-toolbar-title>
        <nuxt-link
          :to="{
            name: 'index',
          }"
          style="color: inherit; text-decoration: inherit"
        >
          {{ "Cultural Japan 管理画面" }}
        </nuxt-link>
      </v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" bottom temporary>
      <v-list>
        <v-list-item
          link
          :to="{ name: item.value }"
          v-for="(item, key) in items"
          :key="key"
          exact
        >
          <v-list-item-header>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-header>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container>
        <slot />
      </v-container>
    </v-main>
    <v-footer class="bg-grey-lighten-1 mt-10">
      <v-row justify="center" no-gutters>
        <v-col class="text-center text-white my-4" cols="12">
          {{ new Date().getFullYear() }} — <strong>Cultural Japan</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>
<script setup lang="ts">
definePageMeta({
  layout: "custom",
});

const drawer = ref<boolean>(false);

const items = [
  {
    title: "HOME",
    value: "index",
  },
  {
    title: "アイテム更新",
    value: "item",
  },
  {
    title: "IIIFコレクションの更新",
    value: "iiif",
  }
];
</script>

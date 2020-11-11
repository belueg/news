<template>
  <div>
    <v-app-bar color="deep-purple accent-4" dense dark>
      <v-toolbar-title>News now</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <a
          href="https://github.com/belueg/"
          class="text-decoration-none heart-color"
          target="_blank"
          title="visit this project's repo"
        >
          <v-icon>
            mdi-heart
          </v-icon>
        </a>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  name: 'Navbar'
}
</script>

<style lang="scss" scoped>
.heart-color {
  color: white;
}
</style>

<template>
  <div class="Modal">
    <div class="text-center">
      <v-dialog v-model="dialog" persistent width="500">
        <v-card>
          <v-card-title
            class="headline grey lighten-2 d-flex justify-space-between"
          >
            <h3>Privacy Policy</h3>
            <v-btn color="primary" text @click="$parent.dialog = false">
              X
            </v-btn>
          </v-card-title>

          <v-card-text>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat. Duis aute irure dolor in
            reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
            pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
            culpa qui officia deserunt mollit anim id est laborum.
          </v-card-text>

          <v-divider></v-divider>

          <v-card-actions>
            <v-spacer></v-spacer>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    dialog: Boolean
  }
}
</script>

<style lang="scss" scoped>
.Modal {
}
</style>

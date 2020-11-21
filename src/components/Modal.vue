<template>
  <div class="Modal">
    <div class="text-center">
      <v-dialog v-model="dialog" persistent width="500">
        <v-card>
          <v-card-title class="headline blue lighten-2 d-flex justify-end">
            <v-btn color="primary" text @click="$parent.dialog = false">
              X
            </v-btn>
            <h3 class="Modal-title">{{ title }}</h3>
          </v-card-title>

          <v-card-text class="Modal-content">
            {{ content }}
          </v-card-text>

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
  name: "Modal",
  props: {
    dialog: Boolean,
    title: String,
    content: String
  }
};
</script>

<style lang="scss" scoped>
.Modal {
  &-title {
    font-size: 18px;
    margin: 10px;
    text-align: center;
  }

  &-content {
    margin-top: 20px;
    margin-bottom: 20px;
  }
}
</style>

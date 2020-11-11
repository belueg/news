<template>
  <div class="CardNew">
    <v-card class="mx-auto" height="436px" max-width="344">
      <v-img :src="imgURL" height="200px"></v-img>

      <v-card-title>
        {{ title | max40Letters }}
      </v-card-title>

      <v-card-subtitle> </v-card-subtitle>

      <v-card-actions>
        <v-btn color="orange lighten-2" @click="dialog = true" text>
          Read
        </v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians, he promised more than he
            could deliver. You won't have time for sleeping, soldier, not with
            all the bed making you'll be doing. Then we'll go with that data
            file! Hey, you add a one and two zeros to that or we walk! You're
            going to do his laundry? I've got to find a way to escape.
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
    <Modal :dialog="dialog" />
  </div>
</template>

<script>
import Modal from '@/components/Modal'

export default {
  name: 'NewCard',
  components: {
    Modal
  },
  data: () => ({
    show: false,
    dialog: false
  }),
  props: {
    title: String,
    imgURL: String
  },
  filters: {
    max40Letters(value) {
      return value.slice(0, 60) + '...'
    }
  }
}
</script>

<style lang="scss" scoped></style>

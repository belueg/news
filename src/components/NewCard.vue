<template>
  <div class="CardNew">
    <v-card class="mx-auto" height="auto" max-width="344">
      <v-img :src="imgURL" height="200px"></v-img>

      <v-card-title>
        {{ title | max40Letters }}
      </v-card-title>

      <v-card-subtitle> </v-card-subtitle>

      <v-card-actions>
        <v-btn color="orange lighten-2" @click="dialog = true" text>
          PREVIEW
        </v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text height="auto">
            Link:
            <a :href="url" target="_blank">{{ url }}</a>
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
    <Modal :dialog="dialog" :title="title" :content="content" />
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
    imgURL: String,
    content: String,
    url: String
  },
  filters: {
    max40Letters(value) {
      return value.slice(0, 60) + '...'
    }
  }
}
</script>

<style lang="scss" scoped>
.CardNew {
  .hideOverflow {
    overflow: hidden;
  }
}
</style>

<template>
  <v-container>
    <h3 class="text-center mt-4 mainHeading">
      Latest news about Bitcoin from all around the world
    </h3>
    <v-row>
      <v-col
        v-for="article in info"
        cols="12"
        sm="4"
        height="100%"
        :key="article.title"
      >
        <NewCard
          :title="article.title"
          :imgURL="article.urlToImage"
          :content="article.content"
          :url="article.url"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
/* eslint-disable */

// @ is an alias to /src
import axios from 'axios'
import NewCard from '@/components/NewCard.vue'
export default {
  name: 'Home',
  components: {
    NewCard
  },
  data() {
    return {
      info: []
    }
  },
  mounted() {
    axios
      .get(
        `http://newsapi.org/v2/everything?q=bitcoin&from=4${this.currentDay()}&sortBy=publishedAt&apiKey=da1bf487186b48bea0ccbcc4c336926b`
      )
      .then(response => (this.info = response.data.articles))

    console.log(this.info)
  },
  computed: {
    cardTitle() {
      return this.info.map(i => i.title.slice(0, 50) + '...')
    }
  },
  methods: {
    currentDay: function() {
      console.log(new Date())
      return new Date().toISOString().split('T')[0]
    }
  }
}
</script>

<style lang="scss" scoped>
.mainHeading {
  font-size: 35px;
}
</style>

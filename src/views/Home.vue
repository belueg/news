<template>
  <v-container>
    <h3 class="text-center mt-4">Latest news from all around the world</h3>
    <!-- <div v-for="article in info" :key="article.title">
      {{ article.author }}:
    </div> -->
    <div v-for="article in info" :key="article.title">
      <NewCard :title="article.title" :imgURL="article.urlToImage" />
    </div>
  </v-container>
</template>

<script>
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
      info: null
    }
  },
  mounted() {
    axios
      .get(
        'http://newsapi.org/v2/everything?q=bitcoin&from=2020-10-11&sortBy=publishedAt&apiKey=da1bf487186b48bea0ccbcc4c336926b'
      )
      .then(response => (this.info = response.data.articles))
  }
}
</script>

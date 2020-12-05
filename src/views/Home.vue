<template>
  <div>
 
    <v-container>
      <h3 class="text-center mt-4 mainHeading">
        Latest news about Bitcoin from all around the world
      </h3>
      <h4 v-if="loading">Loading....</h4>
      <v-row>
        <v-col
          v-for="article in info"
          cols="12"
          sm="4"
          height="100%"
          :key="article.id"
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
  </div>
</template>

<script>
/* eslint-disable */

// @ is an alias to /src
import axios from 'axios'
import shortid from 'shortid'
import NewCard from '@/components/NewCard.vue'
export default {
  name: 'Home',
  components: {
    NewCard
  },
  data() {
    return {
      info: [],
      loading: false
    }
  },
  mounted() {
    this.loading = true
    axios
      .get(
        `http://newsapi.org/v2/everything?q=bitcoin&from=4${this.currentDay()}&sortBy=publishedAt&apiKey=da1bf487186b48bea0ccbcc4c336926b`
      )
      .then(response => {
        this.loading = false
        this.info = response.data.articles
      })
      .then(() => this.info.map(article => (article.id = shortid.generate())))
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
    },
    closeCookiesMsg() {
      this.$refs.cookies.style.visibility = 'hidden'
    }
  }
}
</script>

<style lang="scss" scoped>
.mainHeading {
  font-size: 35px;
}

.cookies {
  width: 100%;
  background-color: #ffa5008c;
  padding: 20px 10px;
  margin: 0;
  display: flex;
  justify-content: space-between;
  p {
    margin: 0;
  }
  &-btn {
    text-decoration: underline;
    &:focus {
      outline: none;
    }
  }
}
</style>

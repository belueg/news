<template>
  <v-app>
    <Navbar />
    <cookie-law theme="dark-lime"></cookie-law>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar'
import CookieLaw from 'vue-cookie-law'

export default {
  name: 'App',

  components: {
    Navbar,
    CookieLaw
  },

  data: () => ({
    //
  })
}
</script>

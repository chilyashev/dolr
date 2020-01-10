<template>
  <v-app>
    <v-content>
      <v-container>
        <v-row>
          <v-col
            cols="12"
            offset="0"
            xl="6"
            offset-xl="3"
          >
            <nuxt />
          </v-col>
        </v-row>
      </v-container>
    </v-content>
    <Footer/>
  </v-app>
</template>

<script>
import Footer from  '~/components/Footer'

export default {
  components: {Footer},
  data() {
    return {
    };
  }
};
</script>

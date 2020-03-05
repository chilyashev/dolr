<template>
  <v-app>
    <v-content>
      <v-container>
        <div class="text-center display-3 font-weight-thin mb-5">
          <div class="mask">
            <img src="~/static/mask.png" />
          </div>Да отида ли на работа днес?
        </div>
        <v-row>
          <v-col cols="12" offset="0" xl="6" offset-xl="3">
            <nuxt />
          </v-col>
        </v-row>
      </v-container>
    </v-content>
    <Footer />
  </v-app>
</template>

<script>
import Footer from "~/components/Footer";

export default {
  components: { Footer },
  data() {
    return {};
  }
};
</script>
<style lang="scss">
.mask {
  display: inline-block;
  position: relative;
  left: 66px;
  top: 50px;
  img {
    width: 100px;
  }
}
</style>
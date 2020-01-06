<template>
  <v-app>
    <v-content>
      <v-container>
        <div class="text-center display-3 font-weight-thin mb-5">Да отида ли на работа днес?</div>
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
    <v-footer >
      <v-spacer></v-spacer>
      <span class="font-italic font-weight-light">
        Направено с
        <span class="font-regular font-weight-regular" style="font-style: normal; color:red">❤</span> в работно време &copy; 2020
      </span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
    };
  }
};
</script>

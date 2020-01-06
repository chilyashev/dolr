<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6 class="mb-9">
      <div class="display-4 font-weight-black text-center">Да.</div>
    </v-flex>
    <v-flex xs12 sm8 md6>
      <div class="font-weight-normal text-center">
        <small>{{ctaText}}, може да опитате и с
        <nuxt-link to="/assess">подробния тест</nuxt-link> или пък да се върнете <nuxt-link to="/">към началото</nuxt-link>.</small>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import Answer from "~/components/Answer";

export default {
  name: "42",
  data() {
    return {
      texts: [
          "Ако все още се колебаете",
        "Ако и вие почувствахте пълна изненада",
      ]
    };
  },
  computed: {
    ctaText() {
      const length = this.texts.length;
      const index = Math.floor(Math.random() * length);
      return this.texts[index];
    }
  }
};
</script>

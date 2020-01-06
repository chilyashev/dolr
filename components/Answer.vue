<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <div class="text-center mb-9">
        <p class="display-4 font-weight-black" v-if="goToWork">Да.</p>
        <p class="display-4 font-weight-black" v-else>Не.</p>
        <p class="display-1 font-weight-thin">{{subTitle}}</p>
      </div>
      
      <div class="text-center">
        <small>Резултатите не покриват очакванията? <a color="primary" @click="resetTest">Тествай се отново!</a></small>
      </div>

    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: "Answer",
  data() {
    return {
      answers: {
        yes: [
            "Хващай пътя и отивай на работа!",
            "Отивай на работа!",
            ],
        no: [
          "Остани, почини си, пий една вода.",
          "Ако е толкова важно, някой друг ще го свърши.",
        ]
      }
    };
  },
  props: {
    goToWork: {
      required: true,
      type: Boolean,
      default: true
    }
  },
  methods: {
    resetTest() {
      this.$emit("reset");
    }
  },
  computed: {
    subTitle() {
      const index = this.goToWork ? "yes" : "no";
      const answers = this.answers[index];
      const answerIndex = Math.floor(Math.random() * answers.length);

      return answers[answerIndex];
    }
  }
};
</script>
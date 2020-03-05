<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6 v-if="!showAnswer" class="mb-5">
      <div class="text-center"></div>

      <p>
        По-долу ще намерите въпроси, които да помогнат с правилния избор. Може и да се върнете
        <nuxt-link to="/">към началото</nuxt-link>.
      </p>
    </v-flex>
    <v-flex xs12 sm8 md6 v-if="!showAnswer">
      <div class="text-center"></div>
      <v-card>
        <v-card-title class="headline" style="word-break: keep-all">{{currentQuestion.question}}</v-card-title>
        <v-card-subtitle>Въпрос: {{currentQuestionIndex+1}}/{{totalQuestions}}</v-card-subtitle>
        <v-card-text>
          <v-radio-group v-model="currentAnswer">
            <v-radio
              v-for="(a, i) in currentQuestion.answers"
              :key="`answer_${currentQuestionIndex}_${i}`"
              :label="a.text"
              :value="a.points"
            ></v-radio>
          </v-radio-group>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn color="primary" @click="nextQuestion" v-if="isLastQuestion">Напред</v-btn>
          <v-btn color="primary" @click="nextQuestion" v-else>Към резултатите</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
    <Answer :goToWork="goToWork" v-if="showAnswer" @reset="reset" />
    <v-snackbar
      v-model="snackbar"
    >
      {{ snackbarText }}
      <v-btn
        color="pink"
        text
        @click="snackbar = false"
      >
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </v-snackbar>
  </v-layout>
</template>

<script>
import Answer from "~/components/Answer";

export default {
  name: "assess",
  components: { Answer },
  data() {
    return {
      snackbarText: '',
      snackbar: false,
      questions: [
        {
          question: "Страх ли ви е от вируса?",
          type: "single",
          answers: [{ text: "Да", points: -100 }, { text: "Не", points: 50 }]
        },
        {
          question: "Имате ли маска?",
          type: "single",
          answers: [{ text: "Да", points: -100 }, { text: "Не", points: 50 }]
        },
        {
          question: "Можете ли да живеете без заплата?",
          type: "single", // Това ще се използва някой друг път
          answers: [{ text: "Да", points: -100 }, { text: "Не", points: 100 }]
        },
        {
          question: "Имате ли богат роднина, който да ви издържа?",
          type: "single",
          answers: [{ text: "Да", points: -100 }, { text: "Не", points: 100 }]
        },
        {
          question: "Имате ли човек в НАП?",
          type: "single",
          answers: [{ text: "Да", points: -50 }, { text: "Не", points: 50 }]
        }
      ],
      currentQuestionIndex: 0,
      currentAnswer: null,
      totalPoints: 0,
      showAnswer: false,
      goingToWorkScore: 49
    };
  },
  mounted() {
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionIndex];
    },
    isLastQuestion() {
      const lastIndex = this.questions.length - 1;
      return this.currentQuestionIndex + 1 <= lastIndex;
    },
    goToWork() {
      return this.totalPoints >= this.goingToWorkScore;
    },
    totalQuestions() {
      return this.questions.length;
    }
  },
  methods: {
    reset() {
      this.currentAnswer = null;
      this.currentQuestionIndex = 0;
      this.totalPoints = 0;
      this.showAnswer = false;
    },
    nextQuestion() {
      if(this.currentAnswer === undefined || this.currentAnswer === null) {
        this.snackbarText = 'Айде да избереш нещо, а?';
        this.snackbar = true;
        return;
      }
      this.snackbarText = '';
      this.snackbar = false;
      const lastIndex = this.questions.length - 1;
      this.totalPoints += this.currentAnswer;
      if (this.currentQuestionIndex + 1 <= lastIndex) {
        this.currentQuestionIndex++;
      } else {
        this.gradeQuestions();
      }
    },
    gradeQuestions() {
      this.showAnswer = true;
    }
  }
};
</script>

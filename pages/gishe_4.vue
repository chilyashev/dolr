<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <div class="font-weight-normal text-center">
        <small>До края на мъките остават</small>
      </div>
    </v-flex>
    <v-flex xs12 sm8 md6 class="mb-9">
      <div class="display-4 font-weight-black text-center">{{timeLeftFormatted}}</div>
    </v-flex>
    <v-flex>
      Ама аз не работя
      до
      <a @click="changeEnd">{{endHour}}</a>!
      <v-combobox v-model="endHour" :items="hours" v-if="editingEnd" @change="updateTimesettings" label="Мъките свършват в" />

    </v-flex>
    <v-flex>
      <small>
        Отказах се, искам
        <nuxt-link to="/">към началото</nuxt-link>.
      </small>
    </v-flex>
    <v-snackbar v-model="snackbar">
      {{ snackbarText }}
      <v-btn color="pink" text @click="snackbar = false">
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </v-snackbar>
  </v-layout>
</template>

<script>
const endTexts = ["Тук не е работа", "Мъката приключи!", "Край!"];
export default {
  name: "gishe_4",
  layout: "empty",
  data() {
    return {
      snackbarText: "",
      snackbar: false,
      endHour: "18:00",
      beautifulEnd: { hour: 18, minutes: 0 },
      timeLeft: 0,
      timerInterval: null,
      editingEnd: false,
      hours: []
    };
  },
  mounted() {
    let alterEgo = this;
    this.updateLeftTime();
    this.timerInterval = setInterval(() => {
      alterEgo.updateLeftTime();
    }, 899);

    this.hours = [];
    for (let hour = 0; hour <= 23; hour++) {
      let hourFormatted = hour.toString().padStart(2, "0");
      this.hours.push(`${hourFormatted}:00`);
    }
  },
  computed: {
    timeLeftFormatted() {
      if (this.timeLeft <= 0) {
        const index = Math.floor(Math.random() * endTexts.length)
        clearInterval(this.timerInterval)
        return endTexts[index];
      }
      let seconds = Math.floor(this.timeLeft % 60)
        .toString()
        .padStart(2, "0");
      let minutes = Math.floor((this.timeLeft / 60) % 60)
        .toString()
        .padStart(2, "0");
      let hours = Math.floor((this.timeLeft / 3600) % 24)
        .toString()
        .padStart(2, "0");

      return `${hours}:${minutes}:${seconds}`;
    }
  },
  methods: {
    updateLeftTime() {
      let thisMoment = new Date();
      let theEnd = new Date().setHours(
        // This is the end, beautiful friend
        this.beautifulEnd.hour,
        this.beautifulEnd.minutes,
        0,
        0
      );
      this.timeLeft = (theEnd - new Date()) / 1000;
    },
    changeEnd() {
      this.editingEnd = true;
    },
    updateTimesettings() {
      // Парсироваме часа, както е въведен от гражданина
      const timelessRegex = /^(\d{1,2}):(\d{2})$/;
      let endMatch = this.endHour.match(timelessRegex);
      const noTimeLikeThePresent = new Date();

      // Проверяваме дали е попълнена правилната молба
      try {
        const endHour = parseInt(endMatch[1]);
        const endMinute = parseInt(endMatch[2]);

        let newEnd = new Date().setHours(endHour, endMinute, 0, 0);

        if (noTimeLikeThePresent.getHours() > endHour || new Date() > newEnd) {
          this.tukNeEInformacia(
            "И на мен ми се иска вече да е свършило, ама не е."
          );
          this.endHour = "18:00";
          this.beautifulEnd = { hour: 18, minutes: 0 };
          return;
        }
        this.beautifulEnd.hour = endHour;
        this.beautifulEnd.minutes = endMinute;

        this.editingEnd = false;
      } catch (eSaStanaEdna) {
        this.tukNeEInformacia(
          "Гражданино, молбата ви е попълнена грешно. Опитайте пак"
        );
        this.endHour = "18:00";
      }
    },
    tukNeEInformacia(vikamMu) {
      this.snackbarText = vikamMu;
      this.snackbar = true;
    }
  }
};
</script>
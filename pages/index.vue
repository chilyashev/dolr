<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm6 md4 lg4>
      <v-sheet class="pa-9" elevation="1">
        <p>Всеки ден този въпрос си задават милиони българи.</p>
        <p>
          Благодарение на напреднал изкуствен интелект и естествена липса на желание за работа създадохме платформа,
          която ще ви помогне да вземете правилното решение!<br>
          Тъй като най-вероятно
          <del>бързате</del> закъснявате за работа, предлагаме две решения:
        </p>
        <v-row>
          <v-col cols="12" sm="6">
            <v-card>
              <v-card-title>Бързо решение&trade;</v-card-title>
              <v-card-text>
                <ul>
                  <li>Отнема малко време</li>
                  <li>100% вярно в част от случаите</li>
                </ul>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" nuxt to="/42">Към бързото решение</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12" sm="6">
            <v-card>
              <v-card-title>Подробен тест</v-card-title>
              <v-card-text>
                <ul>
                  <li>Отнема малко повече време</li>
                  <li>100% вярно в същата част от случаите</li>
                </ul>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" nuxt to="/assess">Към теста</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-sheet>
    <small class="text-left">* Бързото решение може да ви изненада!</small>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  components: {}
};
</script>

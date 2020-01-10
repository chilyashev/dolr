<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm6 md4 lg4>
      <v-sheet class="pa-9" elevation="1">
        <p>Всеки ден този въпрос си задават милиони българи.</p>
        <p>
          Благодарение на напреднал изкуствен интелект и естествена липса на желание за работа създадохме платформа,
          която ще ви помогне да вземете правилното решение!
          <br />Тъй като най-вероятно
          <del>бързате</del> закъснявате за работа, предлагаме две решения:
        </p>
        <v-row>
          <v-col cols="12" sm="6">
            <v-card tile>
              <v-card-title>Бързо решение&trade;</v-card-title>
              <v-card-text>
                <ul>
                  <li>Отнема малко време</li>
                  <li>100% вярно в част от случаите</li>
                  <li>Използва само 100 грама блокчейн</li>
                </ul>
              </v-card-text>
            </v-card>
            <v-btn color="primary" nuxt to="/42" block>Към бързото решение</v-btn>
          </v-col>
          <v-col cols="12" sm="6">
            <v-card tile>
              <v-card-title>Подробен тест</v-card-title>
              <v-card-text>
                <ul>
                  <li>Отнема малко повече време</li>
                  <li>100% вярно в същата част от случаите</li>
                  <li>Използва 250 грама чист био-блокчейн</li>
                </ul>
              </v-card-text>
            </v-card>
            <v-btn color="primary" nuxt to="/assess" block>Към теста</v-btn>
          </v-col>
        </v-row>
        <v-row class="mt-9">
          <v-col>
            <h3>Помощ! Отидох на работа! Какво да правя сега?</h3>
            Спокойно, погрижили сме се и за вашия случай. Заповядяйте към <nuxt-link to="gishe_4">гише №4</nuxt-link>.
          </v-col>
        </v-row>
      </v-sheet>
      <p>
        <small class="text-left">* Бързото решение може да ви изненада!</small>
        <br />
        <small
          class="text-left"
        >** Ако днес сте се минали да отидете на работа, опитайте теста отново утре. А дотогава може да опитате <a href="https://lmgtfy.com/?q=%D0%BF%D0%B0%D1%81%D0%B8%D0%B0%D0%BD%D1%81+%D0%B8+%D0%BC%D0%B8%D0%BD%D0%B8%D1%87%D0%BA%D0%B8">това</a>.</small>
      </p>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  components: {}
};
</script>

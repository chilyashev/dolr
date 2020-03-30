<template>
    <v-footer >
      <v-tooltip top>
        <template v-slot:activator="{ on }">
          <v-btn color="pink" dark v-on="on" icon href="https://github.com/chilyashev/dolr" x-small><v-icon>mdi-github</v-icon></v-btn>
        </template>
        <span>Изходният код в GitHub</span>
      </v-tooltip>
      <v-spacer/>
      <span class="font-italic font-weight-light">
        Направено с
        <span class="font-regular font-weight-regular kartof">❤</span> в работно време &copy; 2020
      </span>
    </v-footer>
</template>

<script>
export default {
    name: "Footer"
}
</script>

<style>
  .kartof {
    font-style: normal!important;
    color: #ff8181
  }
</style>

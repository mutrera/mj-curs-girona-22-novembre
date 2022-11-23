<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col style="background-color:black">
          <v-btn dark to="/">Inici</v-btn>
          <v-btn dark to="/tasques">Tasques</v-btn>
          <v-btn dark to="/textos">Textos</v-btn>
        </v-col>
      </v-row>
    </v-container>
    <v-main>
      <nuxt/>
    </v-main>
  </v-app>
</template>

 
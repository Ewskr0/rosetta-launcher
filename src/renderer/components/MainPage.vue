<template>
  <v-app id="inspire" dark>
    <sideBar></sideBar>
    <v-content class="main">
      <v-container grid-list-md text-xs-center fill-height>
        <v-layout row wrap>
          <v-flex xs12>
            <v-card>
              <v-card-title class="title text-xs-center">
                <h1> Rosetta Laucnher
                </h1>
              </v-card-title>
            </v-card>
          </v-flex>
          <v-flex xs12>
            <v-card>
              <v-img src="/static/image/background1.jpg" height="308px"></v-img>
              <v-card-title class="title">
                <h3>Derniere MAJ: </h3>
                <p class="text-xs-left">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Ratione tempora sed, at suscipit officia ipsa nam dolorum cum, quibusdam sint officiis eos veritatis voluptatibus, porro dicta cumque doloribus molestias perferendis!</p>
              </v-card-title>
            </v-card>
          </v-flex>
          <v-flex xs12>
            <v-layout align-start row>
              <v-btn large color="teal darken-1">Windows</v-btn>
              <v-btn large color="light-blue accent-2">Mac</v-btn>
              <v-btn large color="blue-grey lighten-2">Linux</v-btn>
              <v-spacer></v-spacer>
              <v-btn large color="green darken-2">Lancer</v-btn>
            </v-layout>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
  import SideBar from './SideBar.vue'
  
  export default {
    components: {
      SideBar
    },
    data: () => ({
      drawer: null
    }),
    props: {
      source: String
    }
  }
</script>

<style>
  ::-webkit-scrollbar {
    display: none;
  }
  
  .main {
    padding-left: 80px !important;
  }
  
  h1 {
    width: 100%;
    text-align: center;
  }
</style>
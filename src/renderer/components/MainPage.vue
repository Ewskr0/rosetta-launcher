<template>
  <v-app id="inspire" dark>
    <TitleBar></TitleBar>
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
              <v-btn large color="teal darken-1" @click="getPath()">
                <v-icon>cloud_download</v-icon>
                Télecharger
              </v-btn>
              <v-layout row wrap>
                <v-container grid-list-xs class="containerInfo">
                  <v-flex xs12>
                    <h3 class="text-lg-left">download status: </h3>
                  </v-flex>
                  <v-flex xs12>
                    <v-progress-linear color="success" class="progressBar" v-model="progresValue"></v-progress-linear>
                  </v-flex>
                </v-container>
              </v-layout>
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
  import TitleBar from './TitleBar.vue'
  
  export default {
    components: {
      SideBar,
      TitleBar
    },
    data: () => ({
      drawer: null,
      progresValue: 85
    }),
    props: {
      source: String
    },
    methods: {
      getPath () {
        const {
          dialog
        } = require('electron').remote
        let path = dialog.showOpenDialog({ properties: ['openDirectory'] })
        console.log(path)
      }
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
  
  .containerInfo {
    padding-top: 0!important;
    padding-bottom: 0!important;
  }
  
  .progressBar {
    margin-top: 5px!important;
  }
</style>
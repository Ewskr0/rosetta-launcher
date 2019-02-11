<template>
  <v-app id="inspire" dark>
    <TitleBar></TitleBar>
    <sideBar></sideBar>
    <v-content class="main">
      <v-container grid-list-md fill-height>
        <v-layout row wrap>
          <v-flex xs12>
            <v-card>
              <v-card-title class="title text-xs-center">
                <h1> Rosetta Launcher
                </h1>
              </v-card-title>
            </v-card>
          </v-flex>
          <v-flex xs12>
            <v-card>
              <v-img src="/static/image/background1.jpg" height="308px"></v-img>
              <v-card-title class="title">
                <v-flex xs12 justify-start>
                  <h3>Derniere MAJ:</h3>
                </v-flex>
                <v-flex xs12>
                  <p>Rosetta passe en version 2.50 !</p>
                </v-flex>
              </v-card-title>
            </v-card>
          </v-flex>
          <v-flex xs12>
            <v-layout align-start row>
              <v-layout row wrap>
                <v-container grid-list-xs class="containerInfo">
                  <v-flex xs12>
                    <h3 class="text-lg-left">download status: {{ progressValue}} %</h3>
                  </v-flex>
                  <v-flex xs12>
                    <v-progress-linear color="success" class="progressBar" v-model="progressValue"></v-progress-linear>
                  </v-flex>
                </v-container>
              </v-layout>
              <v-spacer></v-spacer>
              <v-btn large color="green darken-2" @click="getPath()">{{ textBtn}}</v-btn>
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
      path: '',
      progressValue: 85,
      status: ['Lancer', 'Mise à jour', 'Installer'],
      textBtn: ''
    }),
    props: {
      source: String
    },
    created: function () {
      this.textBtn = this.status[0]
      this.loadPath()
    },
    methods: {
      getPath () {
        const {
          dialog
        } = require('electron').remote
        let path = dialog.showOpenDialog({
          properties: ['openDirectory']
        })
        if (path[0]) {
          let data = JSON.stringify(path[0])
          let fs = require('fs')
          fs.writeFileSync('./static/json/path.json', data)
          this.path = path
        }
      },
      loadPath () {
        let fs = require('fs')
        let obj = JSON.parse(fs.readFileSync('./static/json/path.json', 'utf8'))
        if (obj) {
          this.path = obj
          console.log('installation folder: ' + this.path)
        }
      },
      DownloadFiles () {
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
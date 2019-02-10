<template>
  <v-layout row>
    <v-flex xs12 titlebar>
      <v-card dark tile flat color="grey darken-4">
        <v-layout row wrap>
          <v-flex x4>
            <v-card-text class="font-weight-medium">Rosetta Launcher</v-card-text>
          </v-flex>
          <v-spacer></v-spacer>
          <div class="window-controls">
            <v-btn flat icon @click="minimizeWindow()">
              <v-icon>branding_watermark</v-icon>
            </v-btn>
            <v-btn flat icon @click="closeWindow()">
              <v-icon>close</v-icon>
            </v-btn>
          </div>
        </v-layout>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data: () => ({
      drawer: null
    }),
    props: {
      source: String
    },
    methods: {
      closeWindow () {
        const remote = require('electron').remote
        let w = remote.getCurrentWindow()
        w.close()
      },
      minimizeWindow () {
        const remote = require('electron').remote
        let w = remote.getCurrentWindow()
        w.minimize()
      }
    }
  }
</script>

<style>
  .titlebar {
    height: 53px;
    -webkit-app-region: drag;
  }
  
  .window-controls {
    height: 100%;
    -webkit-app-region: no-drag;
  }
</style>
<template>
  <v-navigation-drawer dark permanent mini-variant fixed class="sidebar">
    <v-list>
      <v-list-tile @click="getPath()" title="Reparer">
        <v-list-tile-action>
          <v-icon>build</v-icon>
        </v-list-tile-action>
      </v-list-tile>
      <v-list-tile @click="getPath()" title="Changer de dossier d'installation">
        <v-list-tile-action>
            <v-icon>folder</v-icon>
        </v-list-tile-action>
      </v-list-tile>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
  export default {
    inherit: true,
    data () {
      return {
        drawer: true,
        right: null
      }
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
      getEmpty () {
      }
    }
  }
</script>

<style>
  .sidebar {
    margin-top: 53px!important;
  }
</style>
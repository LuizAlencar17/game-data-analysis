<template>
  <v-container
    id="dashboard"
    fluid
    tag="section"
  >
    <v-row>
      <v-col
        cols="8"
        lg="6"
      >
        <base-material-chart-card
          :data="informationPackageOne.data"
          :options="informationPackageOne.options"
          :responsive-options="informationPackageOne.responsiveOptions"
          color="#E91E63"
          hover-reveal
          type="Line"
        >
          <template v-slot:reveal-actions>
            <v-tooltip bottom>
              <template v-slot:activator="{ attrs, on }">
                <v-btn
                  v-bind="attrs"
                  color="info"
                  icon
                  v-on="on"
                >
                  <v-icon
                    color="info"
                  >
                    mdi-refresh
                  </v-icon>
                </v-btn>
              </template>

              <span>Refresh</span>
            </v-tooltip>

            <v-tooltip bottom>
              <template v-slot:activator="{ attrs, on }">
                <v-btn
                  v-bind="attrs"
                  light
                  icon
                  v-on="on"
                >
                  <v-icon>mdi-pencil</v-icon>
                </v-btn>
              </template>

              <span>Change Date</span>
            </v-tooltip>
          </template>

          <h4 class="card-title font-weight-light mt-2 ml-2">
            Quantidade de acertos em cada fase
          </h4>

          <p class="d-inline-flex font-weight-light ml-2 mt-1">
            Gráfico de linha
          </p>
        </base-material-chart-card>
      </v-col>

      <v-col
        cols="8"
        lg="6"
      >
        <base-material-chart-card
          :data="informationPackageOne.data"
          :options="informationPackageOne.options"
          :responsive-options="informationPackageOne.responsiveOptions"
          color="#E91E63"
          hover-reveal
          type="Bar"
        >
          <template v-slot:reveal-actions>
            <v-tooltip bottom>
              <template v-slot:activator="{ attrs, on }">
                <v-btn
                  v-bind="attrs"
                  color="info"
                  icon
                  v-on="on"
                >
                  <v-icon
                    color="info"
                  >
                    mdi-refresh
                  </v-icon>
                </v-btn>
              </template>

              <span>Refresh</span>
            </v-tooltip>

            <v-tooltip bottom>
              <template v-slot:activator="{ attrs, on }">
                <v-btn
                  v-bind="attrs"
                  light
                  icon
                  v-on="on"
                >
                  <v-icon>mdi-pencil</v-icon>
                </v-btn>
              </template>
              <span>Change Date</span>
            </v-tooltip>
          </template>

          <h4 class="card-title font-weight-light mt-2 ml-2">
            Quantidade de acertos em cada fase
          </h4>

          <p class="d-inline-flex font-weight-light ml-2 mt-1">
            Gráfico de barras
          </p>
        </base-material-chart-card>
      </v-col>
    </v-row>


    {{data}}
  </v-container>
</template>

<script>
  const axios = require('axios')

  export default {
    name: 'DashboardDashboard',
    data: () => ({
      data: [],
      code: '243243',
      numberDeaths: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      numberCollisions: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      loading: true,
      informationPackageOne: {
        data: {
          labels: ['Fase 1', 'Fase 2', 'Fase 3', 'Fase 4', 'Fase 5', 'Fase 6', 'Fase 7', 'Fase 8', 'Fase 9', 'Fase 10', 'Fase 11', 'Fase 12', 'Fase 13'],
          series: [
            [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
          ],
        },
        options: {
          axisX: {
            showGrid: true,
          },
          low: 0,
          high: 0,
          chartPadding: {
            top: 0,
            right: 5,
            bottom: 0,
            left: 0,
          },
        },
        responsiveOptions: [
          ['screen and (max-width: 640px)', {
            seriesBarDistance: 5,
            axisX: {
              labelInterpolationFnc: function (value) {
                return value[0]
              },
            },
          }],
        ],
      },
    }),
    mounted () {
      this.loadData()
      this.loadAllUsers()
    },
    methods: {
      loadData () {
        for (var i = 0; i < this.informationPackageOne.data.series[0].length; i++) {
          this.informationPackageOne.data.series[0][i] = Math.floor(Math.random() * 1000)
        }
        this.informationPackageOne.options.high = Math.max(...this.informationPackageOne.data.series[0])
      },
      loadAllUsers () {
        axios
          .get('https://teste-57287.firebaseio.com/users/' + this.code + '.json?print=pretty')
          .then(response => {
            this.data = response.data
          })
          .catch(error => {
            console.log(error)
          })
          .finally(() => {
            this.loading = false
            this.configureData (this.data);
          })
      },
      configureData (data) {
        // get user names
        var usersNames = Object.keys(data)
        // checks all users
        for (var i = 0; i < usersNames.length; i++){
          // user
          var user = data[usersNames[i]]
          // get events names
          var eventsNames = Object.keys(user)
          // checks all events
          for (var j = 0; j < eventsNames.length; j++){
              // checks each event
              this.checksEvent (user[eventsNames[j]])
          }
        }
        console.log(this.numberDeaths)
      },
      checksEvent (event) {
        var level = parseInt(event['level'].split("Fase")[1])
        level--
        // deaths
        if(event['died'] == "yes"){
          this.numberDeaths[level]++
        }
        // collisions with enemies
        if(event['collided_with_enemy'] == "enemy"){
          this.numberCollisions[level]++
        }
      }
    },
  }
</script>

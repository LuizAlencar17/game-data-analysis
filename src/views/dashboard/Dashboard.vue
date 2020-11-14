<template>
  <v-container
    id="dashboard"
    fluid
    tag="section"
  >
<v-btn
  class="mt-6"
  text
  color="success"
  @click= "changeChartTypes()"

>
  Change chart types
</v-btn>

    <v-row>
      <v-col
        cols="8"
        lg="6"
      >

        <base-material-chart-card
          :data="numberDeaths"
          :options="informationPackageOne.options"
          :responsive-options="informationPackageOne.responsiveOptions"
          :color="colors[4]"
          hover-reveal
          v-bind:type=getGraph()
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
            Number of deaths
          </h4>

        </base-material-chart-card>
      </v-col>
      <v-col
        cols="8"
        lg="6"
      >
        <base-material-chart-card
          :data="numberCollisions"
          :options="informationPackageOne.options"
          :responsive-options="informationPackageOne.responsiveOptions"
          :color="colors[0]"
          hover-reveal
          v-bind:type=getGraph()
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
            Number of collisions with enemies
          </h4>
        </base-material-chart-card>
      </v-col>


      <v-col
        cols="8"
        lg="6"
      >
        <base-material-chart-card
          :data="numberOfCorrectHit"
          :options="informationPackageOne.options"
          :responsive-options="informationPackageOne.responsiveOptions"
          :color="colors[5]"
          hover-reveal
          v-bind:type=getGraph()
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
            Number of correct hits
          </h4>
        </base-material-chart-card>
      </v-col>

      <v-col
        cols="8"
        lg="6"
      >
        <base-material-chart-card
          :data="numberOfIncorrectHit"
          :options="informationPackageOne.options"
          :responsive-options="informationPackageOne.responsiveOptions"
          :color="colors[2]"
          hover-reveal
          v-bind:type=getGraph()
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
            Number of incorrect hits
          </h4>
        </base-material-chart-card>
      </v-col>

      <v-col
        cols="8"
        lg="6"
      >
        <base-material-chart-card
          :data="this.numberOfBullet"
          :options="informationPackageOne.options"
          :responsive-options="informationPackageOne.responsiveOptions"
          :color="colors[3]"
          hover-reveal
          v-bind:type=getGraph()
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
            Number of knitting shots
          </h4>
        </base-material-chart-card>
      </v-col>
    </v-row>
    <div class="text-center">
      <v-bottom-sheet
        v-model="sheet"
        persistent
      >
        <v-sheet
          class="text-center"
          height="2000px"
        >
          <v-btn
            class="mt-6"
            text
            color="success"
            @click= "sheet = !sheet"

          >
            Continue anyway
          </v-btn>
          <div class="py-3">
            We are loading data
          </div>
          <v-progress-circular
                :rotate="360"
                :size="100"
                :width="15"
                :value="pregressBar"
                color="success"
              >Records:
              {{this.pregressBar}}
              </v-progress-circular>
        </v-sheet>
      </v-bottom-sheet>
    </div>
    </v-container>
</template>

<script>
  const axios = require('axios')

  export default {
    name: 'DashboardDashboard',
    data: () => ({
      colors: [
        '#9C27b0',
        '#00CAE3',
        '#4CAF50',
        '#ff9800',
        '#E91E63',
        '#FF5252',
      ],
      chartTypes: 'Bar',
      sheet: true,
      pregressBar: 0,
      data: [],
      code: '243243',
      numberDeaths: {
          labels: ['Level1', 'Level2', 'Level3', 'Level4', 'Level5', 'Level6', 'Level7', 'Level8', 'Level9', 'Level10', 'Level11', 'Level12', 'Level13'],
          series: [
            [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
          ],
        },
      numberCollisions: {
          labels: ['Level1', 'Level2', 'Level3', 'Level4', 'Level5', 'Level6', 'Level7', 'Level8', 'Level9', 'Level10', 'Level11', 'Level12', 'Level13'],
          series: [
            [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
          ],
        },
      numberOfCorrectHit: {
          labels: ['Level1', 'Level2', 'Level3', 'Level4', 'Level5', 'Level6', 'Level7', 'Level8', 'Level9', 'Level10', 'Level11', 'Level12', 'Level13'],
          series: [
            [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
          ],
        },
      numberOfIncorrectHit: {
          labels: ['Level1', 'Level2', 'Level3', 'Level4', 'Level5', 'Level6', 'Level7', 'Level8', 'Level9', 'Level10', 'Level11', 'Level12', 'Level13'],
          series: [
            [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
          ],
        },
      numberOfBullet: {
          labels: ['Level1', 'Level2', 'Level3', 'Level4', 'Level5', 'Level6', 'Level7', 'Level8', 'Level9', 'Level10', 'Level11', 'Level12', 'Level13'],
          series: [
            [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
          ],
        },
      loading: true,
      informationPackageOne: {
        data: {
          labels: ['Level1', 'Level2', 'Level3', 'Level4', 'Level5', 'Level6', 'Level7', 'Level8', 'Level9', 'Level10', 'Level11', 'Level12', 'Level13'],
          series: [
            [10, 20, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
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
            seriesBarDistance: 1,
            axisX: {
              labelInterpolationFnc: function (value) {
                return value[0]
              },
            },
          }],
        ],
      },
    }),
    mounted() {
      let self = this
      this.loadData()
      this.loadAllUsers()

    },
    methods: {
      showData () {
        setTimeout(() => {
          document.getElementById('menu').click()
        }, 1000);
        setTimeout(() => {
          document.getElementById('menu').click()
          this.sheet = false
        }, 2000);
      },
      getGraph () {
        return this.chartTypes
      },
      changeChartTypes () {
        if(this.chartTypes == 'Bar'){
          this.chartTypes = 'Line'
        }else{
          this.chartTypes = 'Bar'
        }
      },
      loadData () {
        let self = this
        for (var i = 0; i < self.informationPackageOne.data.series[0].length; i++) {
          self.informationPackageOne.data.series[0][i] = Math.floor(Math.random() * 70)
        }
        self.informationPackageOne.options.high = Math.max(...self.informationPackageOne.data.series[0])
      },
      loadAllUsers () {
        let self = this
        axios
          .get('https://teste-57287.firebaseio.com/users/' + self.code + '.json?print=pretty')
          .then(response => {
            self.data =  response.data
          })
          .catch(error => {
            console.log(error)
          })
          .finally(() => {
            self.loading = false
            self.configureData (self.data);
          })
      },
      configureData (data) {
        let self = this
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
              self.checksEvent (user[eventsNames[j]])
              self.pregressBar++
          }
        }
      this.showData ()
      console.log('numberDeaths',self.numberDeaths.series[0])
      console.log('numberOfCorrectHit',self.numberOfCorrectHit.series[0])
      console.log('numberOfIncorrectHit',self.numberOfIncorrectHit.series[0])
      console.log('numberOfBullet',self.numberOfBullet.series[0])
      console.log('numberCollisions',self.numberCollisions.series[0])
      console.log('pregressBar',self.pregressBar)
      },
      checksEvent (event) {
        let self = this
        var level = parseInt(event['level'].split("Fase")[1])
        level--
        if(event['died'] == "yes"){
          self.numberDeaths.series[0][level]++
        }
        if(event['hit_question'] == "yes"){
          self.numberOfCorrectHit.series[0][level]++
        }
        if(event['hit_question'] == "no"){
          self.numberOfIncorrectHit.series[0][level]++
        }
        if(event['button_name'] == "[BTN] Atirar"){
          self.numberOfBullet.series[0][level]++
        }
        if(event['collided_with_enemy'] == "yes"){
          self.numberCollisions.series[0][level]++
        }
      }
    },
  }
</script>
<style scoped>
.v-progress-circular {
  padding: 6%;
  margin-top: 9%
}
</style>

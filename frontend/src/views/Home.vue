<template>
  <div class="home">
    <h1>Last Race Results</h1>
    <div v-for="(result, i) in lastResults" :key="i">{{ result }}</div>
    <!-- <div v-if="lastResults">{{lastResults}}</div> -->
  </div>
</template>

<script>
// @ is an alias to /src

import axios from 'axios'

export default {
  name: 'Home',
  data() {
    return {
      lastResults: null,
    }
  },
  created(){
    var config = {
      method: 'get',
      url: 'http://ergast.com/api/f1/current/last/results.json',
      headers: { }
    };

    axios(config)
    .then(res => {
      this.lastResults = res.data.MRData.RaceTable.Races[0].Results;
      // let raceResult = response.data.MRData.RaceTable.Races[0].Results;
      console.log(this.lastResults);
      
    })
    .catch(function (error) {
      console.log(error);
    });
  },
  components: {

  }
}
</script>

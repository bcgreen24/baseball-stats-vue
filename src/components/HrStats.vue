<template>
  <div class="flex-item">
  <h3>{{ heading }}</h3>
  <table v-if="hrs.leader_hitting_repeater">
    <tr>
      <th>Player</th>
      <th>Home Runs</th>
    </tr>
    <tr v-for="(hr, index) in hrs.leader_hitting_repeater.leader_hitting_mux.queryResults.row" :key="index">
      <td v-if="hrs.leader_hitting_repeater">{{ hr.name_display_first_last}}</td>
      <td v-if="hrs.leader_hitting_repeater">{{hr.hr}}</td>
    </tr>
  </table>
  </div>
</template>

<script>
export default {
  name: 'HrStats',
  data () {
    return {
      heading: 'Baseball Stats 2021',
      hrs: {},
      urls: {
        base_url: "https://lookup-service-prod.mlb.com",
        HRs: "/json/named.leader_hitting_repeater.bam?sport_code=%27mlb%27&results=15&game_type=%27R%27&season=%272021%27&sort_column=%27hr%27&leader_hitting_repeater.col_in=name_display_first_last,hr,player_id",
        }
      };
    },
    created (){
      fetch(this.urls.base_url + this.urls.HRs)
      .then(response => response.json())
      .then(json=> this.hrs = json);
    }
}
</script>
<style>
.flex-item{
  width:100%;
}
table{
  min-width: 300px;
}
</style>

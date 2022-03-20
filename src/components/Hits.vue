<template>
  <div class="flex-item">
  <h3>{{ heading }}</h3>
  <table v-if="hits.leader_hitting_repeater">
    <tr>
      <th>Player</th>
      <th>Hits</th>
    </tr>
    <tr v-for="(hit, index) in hits.leader_hitting_repeater.leader_hitting_mux.queryResults.row" :key="index">
      <td v-if="hits.leader_hitting_repeater" >{{ hit.name_display_first_last }}</td>
      <td v-if="hits.leader_hitting_repeater" >{{ hit.h }}</td>
    </tr>
  </table>
  </div>
</template>

<script>

export default {
  name: 'Hits',
  data () {
    return {
      heading: 'Baseball Stats 2021',
      hits: { },
      urls: {
        base_url: "https://lookup-service-prod.mlb.com",
        Hits: "/json/named.leader_hitting_repeater.bam?sport_code=%27mlb%27&results=15&game_type=%27R%27&season=%272021%27&sort_column=%27h%27&leader_hitting_repeater.col_in=name_display_first_last,h,player_id",
        }
      };
    },
    created (){
      fetch(this.urls.base_url + this.urls.Hits)
      .then(response => response.json())
      .then(json => this.hits = json);
    }
}
</script>
<style>
.flex-item{
  width:100%;
}
table{
  border-collapse: collapse;
  margin-left:auto;
  margin-right:auto;
  min-width:300px;
}
td, th{
  border: solid 1px #ccc;
}
</style>

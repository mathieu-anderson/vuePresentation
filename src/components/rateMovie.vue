<template lang="html">
  <table>
    <tr>
      <td class="rating_head"> Your rating</td>
      <td class="rating_head">{{api_res_number_of_votes}} people's rating</td>
      <td class="rating_head">RandomProfileName's rating</td>
    </tr>
    <tr>
      <td class="rating_values">{{value}}</td>
      <td class="rating_values">{{api_res_rating}}</td>
      <td class="rating_values">1</td>
    </tr>
    <tr>
      <td>
        <a class="button"
          v-on:click="reload()">
            Again?
        </a>
      </td>
      <td>
        <a class="button"
          v-bind:href="go_to_TMDB"
          v-on:mouseover="goToTMDB()"
          target="_blank">
          Fight with {{api_res_number_of_votes}} people?
        </a>
      </td>
      <td>
        <a class="button"
          v-bind:href="go_to_TMDB"
          v-on:mouseover="goToTMDB()"
          target="_blank">
          Fight with RandomProfileName?
        </a>
      </td>
    </tr>
  </table>
</template>

<script>
export default {
  name: 'rateMovie',
  props: [
    'api_res_name',
    'TMDB_api_key',
    'value',
    'api_res_rating',
    'api_res_number_of_votes',
    'api_res_link',
    'api_res_ID'
  ],
  data () {
    return {
      go_to_TMDB: ''
    }
  },
  methods: {
    goToTMDB: function () {
      this.go_to_TMDB = 'https://www.themoviedb.org/movie/' + this.api_res_ID
    }
  }
}
</script>

<style lang="css">
.rating_head {
  font-size: 14pt;
  font-weight: bold;
}

.rating_values {
  font-size: 20pt;
  font-weight: bold;
}

table {
  margin-left: auto;
  margin-right: auto;
}

td {
  padding-left: 20pt;
  padding-right: 20pt;
}

.button {
    -webkit-appearance: button;
    -moz-appearance: button;
    appearance: button;

    text-decoration: none;
    color: initial;

    padding: 15pt;

    font-size: 14px;

    cursor: pointer;

}
</style>

<template lang="html">

<div>

  <div class="wrapper aligner"
    v_if="showAPIRes">
    <img class="aside"
    v-bind:src="api_res_poster">
    <div class="main ">
      <span class="title">{{api_res_name}}</span>
      <br /><br />
      {{api_res_overview}}
    </div>
  </div>
  <br /><br />
  <div class="rate"
    v-if="showRate">
    How do you rate it ?
    <div class="star-rating">
      <label class="star-rating__star"
      v-for="rating in ratings"
      v-bind:class="{selected: ((value >= rating && value != null))}"
      v-on:mouseover="starOver(rating)"
      v-on:mouseout="starOut(rating)"
      v-on:click="setRate(rating)">
      <input
      class="star-rating star-rating__checkbox"
      type="radio"
      v-model="value">
      ♥
      </label>
    </div>
  </div>
  <rateMovie v-if="showTMDB"
  v-bind:value='value'
  v-bond:api_res_name='api_res_name'
  v-bind:api_res_rating='api_res_rating'
  v-bind:api_res_number_of_votes='api_res_number_of_votes'
  v-bind:api_res_link='api_res_link'
  v-bind:api_res_ID='api_res_ID'
  v-bind:TMDB_api_key='TMDB_api_key'>
</rateMovie>

</div>

</template>

<script>
import axios from 'axios'
import rateMovie from './rateMovie'

export default {
  name: 'seeMovie',
  components: {
    rateMovie
  },
  props: [
    'TMDB_api_key',
    'showAPIRes',
    'api_res_name',
    'api_res_overview',
    'api_res_poster',
    'api_res_ID'
  ],
  data () {
    return {
      showRate: true,
      showTMDB: false,
      value: '',
      temp_value: '',
      ratings: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
      api_res_rating: '',
      api_res_number_of_votes: '',
      api_res_link: ''
    }
  },
  methods: {
    starOver: function (index) {
      this.temp_value = this.value
      this.value = index
    },

    starOut: function (index) {
      this.value = this.temp_value
    },

    setRate: function (value) {
      this.temp_value = value
      this.value = value
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.TMDB_api_key}&language=en-US&query=${this.api_res_name}&page=1&include_adult=false`)
        .then(res => {
          this.api_res_rating = res.data.results[0].vote_average
          this.api_res_number_of_votes = res.data.results[0].vote_count
        })
        .then(res => {
          this.showRate = false
          this.showTMDB = true
        })
    }
  }
}

</script>

<style lang="css">

.title {
  font-style: italic;
  font-weight: bolder;
  font-size: 18pt;
}

.wrapper {
    margin-left: 20vw;
    margin-right: 20vw;
    display: -ms-inline-flexbox;
    display: -webkit-inline-flex;
    display: inline-flex;
    -webkit-flex-direction: row;
    -ms-flex-direction: row;
    flex-direction: row;
    -webkit-flex-wrap: nowrap;
    -ms-flex-wrap: nowrap;
    flex-wrap: nowrap;
    -webkit-justify-content: flex-start;
    -ms-flex-pack: start;
    justify-content: flex-start;
    -webkit-align-content: center;
    -ms-flex-line-pack: center;
    align-content: center;
    -webkit-align-items: flex-start;
    -ms-flex-align: start;
    align-items: flex-start;
    }

.aside {
    -webkit-order: 0;
    -ms-flex-order: 0;
    order: 0;
    -webkit-flex: 0 1 auto;
    -ms-flex: 0 1 auto;
    flex: 0 1 auto;
    -webkit-align-self: auto;
    -ms-flex-item-align: auto;
    align-self: auto;
    }

.main {
    width: 30vw;
    text-align: left;
    padding-left: 2vw;
    -webkit-order: 0;
    -ms-flex-order: 0;
    order: 0;
    -webkit-flex: 0 1 auto;
    -ms-flex: 0 1 auto;
    flex: 0 1 auto;
    -webkit-align-self: auto;
    -ms-flex-item-align: auto;
    align-self: auto;
    }

.aligner {
  display: flex;
  align-items: center;
  justify-content: center;
}

.aligner-item {
  max-width: 50%;
}

.star-rating__checkbox {
  position: absolute;
  overflow: hidden;
  clip: rect(0 0 0 0);
  height: 1px;
  width: 1px;
  margin: -1px;
  padding: 0;
  border: 0; }

.star-rating__star {
  display: inline-block;
  padding: 3px;
  vertical-align: middle;
  line-height: 1;
  font-size: 1.5em;
  color: #ababab;
  transition: color .2s ease-out;
}
.star-rating__star:hover {
  cursor: pointer;
}
.star-rating__star.selected {
  color: #c90000;
}
.star-rating__star.disabled:hover {
  cursor: default;
}

</style>

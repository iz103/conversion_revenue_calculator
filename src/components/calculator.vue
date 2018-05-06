<template>
  <div class="calculator">
    <!-- <h1>{{ msg }}</h1> -->
    <h2>What your Revenue Looks like</h2>
    <form class="" action="index.html" method="post">
      <label for="">Enter your Target Monthly Revenue</label>
      <input type="text" v-model='tmr' name="" value="" required>
      <label for="">Enter your conversion rate</label>
      <input type="text" v-model='cr' name="" value="" required placeholder="e.g. 2%">
      <label for="">Enter your typical conversion value (e.g. average cart order size in dollars)</label>
      <input type="text" v-model='cv' name="" value="" required>
    </form>
    <div id="result">
      <h3>Results</h3>
      <p>Revenue Per Visitor: ${{rpv}}</p>
      <p>Number of Target Daily Visitors: {{tdv}} visitors</p>
      <p>Number of daily conversions: {{nc}} sales</p>
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      tmr: '',
      cv: '',
      cr: ''
    }
  },
  computed:  {
    rpv: function () {
      return (this.tdr / this.tdv);
    },
    tdr : function () {
      return (this.tmr / 30);
    },

    nc: function () {
      return (this.tdr / this.cv);
    },

    tdv: function () {
      var ratio_cr = this.cr / 100
      return (this.nc / (this.cr / 100));
    }
  },

  methods: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

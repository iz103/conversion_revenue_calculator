<template>
  <div   class="calculator">
    <div class="container">
      <div class="columns">
        <div class="column is-one-third"></div>
        <div class="column">
          <figure class="image is-128x128">
            <img src="http://hq.gathercustomers.com/assets/img/gather-logo-text-dark.png" alt="">
          </figure>
          <h1 class='title'>Ecommerce ROI Calculator</h1>
          <div class="field">
            <label class="label">Enter your Target Monthly Revenue</label>
            <div class="control">
              <!-- <input class="input" type="text" placeholder="e.g Alex Smith"> -->
              <input class="input" type="number" v-model='tmr' name="" value="" required>
            </div>
          </div>
          <div class="field">
            <label class="label">Enter your conversion rate</label>
            <div class="control">
              <input class="input" type="number" v-model='cr' name="" value="" required placeholder="e.g. 2%">
            </div>
          </div>
          <div class="field">
            <label class="label">Enter your typical conversion value (e.g. average cart order size in dollars)</label>
            <div class="control">
              <input class="input" type="number" v-model='cv' name="" value="" required>
            </div>
          </div>
          <div class="field">
            <label class="label">Enter average cost of acquiring 1 visitor (e.g. average cost per click for Google or Facebook Ads)</label>
            <div class="control">
              <input class="input" type="number" v-model='cpv' name="" value="" required>
            </div>
          </div>
        </div>
        <div class="column"></div>
      </div>
      <div class="columns">
        <div class="column is-one-third">

        </div>
        <div class="column">
          <article class="message is-success">
            <div class="message-header">
              <p>Results</p>
              <!-- <button class="delete" aria-label="delete"></button> -->
            </div>
            <div id="result">
              <br>
              <h5 class="title is-5">Revenue Per Visitor</h5>
              <p>${{rpv || 0}}</p>
              <br>
              <h5 class="title is-5">Number of Target Daily Visitors</h5>
              <p>{{tdv || 0}} visitors</p>
              <br>
              <h5 class="title is-5">Number of daily conversions</h5>
              <p> {{nc || 0}} sales</p>
              <br>
              <h5 class="title is-5">ROI Ratio</h5>
              <p>{{roi || 0}}</p>
            </div>
            <!-- <div class="message-body">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
            </div> -->
          </article>
        </div>
        <div class="column">

        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      tmr: 0,
      cv: 0,
      cr: 0,
      cpv: 0,
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
      var ratioCr = this.cr / 100
      return (this.nc / ratioCr);
    },
    roi: function() {
      var ratioCr = this.cr / 100
      var tdv = this.nc / ratioCr
      console.log('tdv:', tdv);
      var cpdv = this.cpv * tdv
      console.log('cpdv:', cpdv);
      var cpmv = cpdv * 30
      console.log('cpmv:', cpmv);
      var ntmv = this.tmr - cpmv
      console.log('ntmv:', ntmv);
      var as = this.tmr - ntmv
      console.log('as:', as);
      return (this.tmr / as);
    }
  },

  methods: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

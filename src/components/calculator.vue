<template>
  <div   class="calculator">
    <div class="container">
      <div class="columns">
        <div class="column is-one-third">
          <figure class="image is-128x128">
            <a href="http://hq.gathercustomers.com" target="_blank">
              <img src="http://hq.gathercustomers.com/assets/img/gather-logo-text-dark.png" alt="">
            </a>
          </figure>
          <h1 class='title'>Simple ROI Calculator</h1>
          <h4 class='subtitle is-4'>Fill in all fields</h4>
        </div>
        <div class="column">
          <div class="field">
            <label class="label">Enter your Target Monthly Revenue</label>
            <div class="control">
              <!-- <input class="input" type="text" placeholder="e.g Alex Smith"> -->
              <input class="input" type="number" v-model='tmr' name="" value="" required>
            </div>
          </div>
          <div class="field">
            <label class="label">Enter your Conversion Rate</label>
            <div class="control">
              <input class="input" type="number" v-model='cr' name="" value="" required placeholder="e.g. 2%">
            </div>
          </div>
          <div class="field">
            <label class="label">Enter your Typical Conversion Value (e.g. average cart order size in dollars)</label>
            <div class="control">
              <input class="input" type="number" v-model='cv' name="" value="" required>
            </div>
          </div>
          <div class="field">
            <label class="label">Enter Average Cost of Acquiring 1 Visitor (e.g. average cost per click for Google or Facebook Ads)</label>
            <div class="control">
              <input class="input" type="number" v-model='cpv' name="" value="" required>
            </div>
          </div>
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
              <p>~${{Math.ceil(rpv || 0)}}</p>
              <br>
              <h5 class="title is-5">Number of Target Daily Visitors</h5>
              <p>~{{Math.ceil(tdv || 0)}} visitors</p>
              <br>
              <h5 class="title is-5">Number of daily conversions</h5>
              <p>~{{Math.ceil(nc || 0)}} sales</p>
              <br>
              <h5 class="title is-5">ROI Ratio (or Markup)</h5>
              <p>{{(roi || 0).toFixed(2)}}</p>
            </div>
            <!-- <div class="message-body">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur. Aenean ac <em>eleifend lacus</em>, in mollis lectus. Donec sodales, arcu et sollicitudin porttitor, tortor urna tempor ligula, id porttitor mi magna a neque. Donec dui urna, vehicula et sem eget, facilisis sodales sem.
            </div> -->
          </article>
        </div>
      </div>
      <div class="columns">
        <div class="column is-one-third">

        </div>
        <div class="column">
        </div>
        <div class="column">

        </div>
      </div>
    </div>
    <footer class="footer">
      <div class="content has-text-centered">
        <p>
          <strong>Simple ROI Calculator</strong> by <a href="http://hq.gathercustomers.com" target="_blank">Gather. Grow your audience and personalize their experience</a>
        </p>
      </div>
    </footer>
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

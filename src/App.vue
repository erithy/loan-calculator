<template>
  <div id="app">
    <div style="padding: 10px 20px; ">
      <h2 style="margin: 0">Amount to Pay Per month</h2>
    </div>
    <div>
      <form style="padding:20px">
        <br>
        <label>Price($)</label>
        <input type="number" v-model="price" placeholder="Price">
        <br>
        <label>Deposit</label>
        <input type="number" v-model="deposit" placeholder="Deposit">
        <br>
        <label>Interest Rate(%)</label>
        <input type="number" v-model="rate" placeholder="Interest Rate(%)">
        <br>
        <label>Term(Years)</label>
        <input type="number" v-model="term" placeholder="Term(Years)">
        <br>
        <input type="button" @click="calRate" value="Calculate">
      </form>
      <h3>Interest: ${{a}}</h3>
      <h2 style="color: #2c3e50;">
        Monthly Payment: ${{ val }}
      </h2>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      term: 4,
      rate: 1.69,
      price: 1400,
      deposit: 0,
      val: '',
      a: ''
    }
  },
  name: 'App',
  methods: {
    calRate () {
      const payrate = (this.price - this.deposit) * (this.rate / 100) * (this.term * 12)
      this.a = payrate
      this.val = ((payrate + (+(this.price - this.deposit))) / (this.term * 12)).toFixed(3)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 20px;
}
input[type=number], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type=button] {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=button]:hover {
  background-color: #45a049;
}
</style>

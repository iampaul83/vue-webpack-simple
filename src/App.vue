<template>
  <div>

    <div>
      <div v-for="(level, index) in fee_levels">
        <input v-model.number="level.bound" @blur="sort" type="number">: <input v-model.number="level.cost" type="number"> <button v-on:click="removeLevel(index)">delete</button>
      </div>
      <button v-on:click="addLevel">add</button>
      <button v-on:click="sort">sort</button>
    </div>

    <div>{{JSON.stringify(fee_levels)}}</div>
    <div>{{JSON.stringify(postData())}}</div>

  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      fee1: 5,
      fee2: 2,
      cofig1: 5,
      config2: 0, 
      fee_levels: [
        {
          bound: 1200,
          cost: 2999
        },
        {
          bound: 1000,
          cost: 4999
        }
      ]
    }
  },
  methods: {
    greet(event) {
      // `this` inside methods points to the Vue instance
      alert('Hello ' + this.msg + '!')
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName)
      }
    },
    addLevel() {
      this.fee_levels.push({})
    },
    removeLevel(index) {
      this.fee_levels.splice(index, 1)
    },
    sort() {
      this.fee_levels = this.fee_levels.sort((a, b) => a.bound > b.bound)
    },
    postData() {
      let fee_levels = {};
      this.fee_levels.forEach(l => fee_levels[l.bound] = l.cost);
      return {
        fee1: this.fee1,
        fee2: this.fee2,
        config1: this.config1,
        config2: this.config2,
        fee_levels: fee_levels
      }
    }
  },
  computed: {
    
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

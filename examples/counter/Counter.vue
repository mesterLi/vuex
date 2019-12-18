<template>
  <div id="app">
    Clicked: {{ $store.state.count }} times, count is.{{evenOrOdd}}
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
    <button @click="incrementIfOdd">Increment if odd</button>
    <button @click="incrementAsync">Increment async</button>
  </div>
</template>

<script>
import { mapGetters, mapActions, mapState, mapMutations } from 'vuex'

export default {
  computed: {
    ...mapState('test', {
      evenOrOdd: state => {
        console.log('test', state)
        return state
      }
    })
  },
  mounted() {
    console.log(this)
    this.incrementB(100)
  },
  methods: {
    ...mapActions({
      increment: 'test/increment',
      decrement: 'test/decrement',
      incrementIfOdd: 'test/incrementIfOdd',
      incrementAsync: 'test/incrementAsync'
    }),
    ...mapMutations({
      increment: 'increment',
      incrementB: function (commit, payload) {
        console.log(commit, payload)
        commit('increment', payload)
      }
    })
  }
}
</script>

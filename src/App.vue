<script>
import axios from 'axios'
import { state } from './state.js'
import AppMain from "./components/AppMain.vue"
import AppHeader from "./components/AppHeader.vue"
import AppFooter from "./components/AppFooter.vue"
export default {
  name: 'App',
  components: {
    AppMain,
    AppHeader,
    AppFooter
  },
  data() {
    return {
      state
    }
  },
  methods: {
    
  },
  mounted() {
    axios.get(state.url)
      .then(response => {
          this.state.entries = response.data.results
          this.state.info = response.data.info
          console.log(response.data.results)
          console.log(this.state.entries)
      })
  }
}
</script>

<template>
<div class="filter">
   <AppHeader />
  <AppMain />
  <AppFooter />

</div>
 
</template>

<style lang="scss" scoped>
.filter{
  background: rgba(0,0,0,.7);
   height: 100%;
}

</style>

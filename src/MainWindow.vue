<template>
  <Window :title="settings.windowTitle" :width="windowSize.width" :height="windowSize.height" margined v-on:close="exit">
    <Box padded>
      <component :is="currentPage" :settings.sync="settings" @exit="exit" @stop="stop" @start="start"/>
    </Box>
  </Window>
</template>

<script>
import Admin from './pages/Admin'
import CoffeeTime from './pages/CoffeeTime'

export default {
  data () {
    return {
      settings: {
        windowTitle: 'Coffee break',
        header: 'I just need coffee!',
        reason: 'I\'ve been working hard this morning, \nlet me caffeinate please...',
        duration: 10,
        warning: 'Hey! Who told you you could touch that computer ?',
        onCancel: 1,
        closeOnEnd: true
      },
      coffeeTime: false
    }
  },
  computed: {
    currentPage () {
      return this.coffeeTime ? CoffeeTime : Admin
    },
    windowSize () {
      return this.coffeeTime ? {width: 600, height: 100} : {width: 600, height: 800}
    }
  },
  methods: {
    exit () {
      this.$exit();
    },
    start() {
      this.coffeeTime = true
    },
    stop () {
      this.coffeeTime = false
    }
  }
}
</script>

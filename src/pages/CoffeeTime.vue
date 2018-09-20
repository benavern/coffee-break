<template>
  <Box>
    <Group :title="settings.header" margined>
      <Box padded>
        <Text>{{ settings.reason }}</Text>

        <Box horizontal padded>
          <Text>{{ progress | percentage }}</Text>
          <ProgressBar v-bind:value="progress" stretchy/>
        </Box>
      </Box>
    </Group>

    <Box horizontal padded>
      <Box stretchy />
      <Button @click="cancel">Cancel</Button>
    </Box>
  </Box>
</template>

<script>
export default {
  props: ['settings'],
  filters: {
    percentage (val) {
      return `${Math.floor(val)}%`
    }
  },
  data () {
    return {
      progress: 0,
      interval: null
    }
  },
  methods: {
    cancel () {
      if (this.settings.warning) this.$dialogs.msgBoxError('Warning!', this.settings.warning)

      if (this.settings.onCancel === 1) {
        this.$emit('exit')
      } else if (this.settings.onCancel === 2) {
        this.$emit('stop')
      }
    },
    updateProgress () {
      const newVal = this.progress + 100 / (this.settings.duration * 60)
      if (newVal <= 100) {
        this.progress = newVal
      } else {
        this.progress = 100
        if (this.settings.closeOnEnd) {
          this.$emit('exit')
        }
      }
    }
  },
  mounted () {
    this.interval = setInterval(this.updateProgress, 1000)
  },
  beforeDestroy () {
    clearInterval(this.interval)
  }
}
</script>

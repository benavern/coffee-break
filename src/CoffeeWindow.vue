<template>
  <Window title="Example" width="400" height="100" margined v-on:close="close">
    ...
  </Window>
</template>
​
<script>
export default {
  methods: {
    close() {
      this.$root.$destroy();
    }
  }
}
</script>

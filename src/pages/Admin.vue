<template>
  <Box>
    <Group title="Coffee Break Settings" margined>
      <Form padded>
        <TextInput label="Window Title" v-model="settings.windowTitle"/>

        <Separator horizontal />

        <TextInput label="Header" v-model="settings.header"/>

        <Separator horizontal />

        <TextArea label="Your Reason" v-model="settings.reason" />

        <Separator horizontal />

        <Slider label="Duration" min="0" max="60" v-model="settings.duration"/>

        <Separator horizontal />

        <TextInput label="Warning" v-model="settings.warning"/>

        <Separator horizontal />

        <RadioButtons label="On Cancel" :items="['Nothing', 'Close', 'Back To Settings']"
              v-model="settings.onCancel"/>

        <Separator horizontal />

        <Checkbox label="On End" v-model="settings.closeOnEnd">close</Checkbox>
      </Form>
    </Group>

    <Group margined>
      <Box horizontal padded>
        <Button @click="$emit('start')" stretchy>Start</Button>
        <Button @click="credit">Credit</Button>
      </Box>
    </Group>
  </Box>
</template>

<script>
export default {
  props: ['settings'],
  methods: {
    credit () {
      this.$dialogs.msgBox('Credit', 'This app has been made by Benjamin Caradeuc. \nbenjamin.caradeuc.info')
    }
  }
}
</script>

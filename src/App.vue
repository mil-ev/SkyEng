<template>
  <div id="app">
    <message :msgs="dataMessages"></message>
    <messages :msgs="dataMessages"></messages>
    <send-message :msgs="dataMessages"></send-message>

  </div>
</template>

<script>
import Message from './components/Message'
import Messages from './components/Messages'
import SendMessage from "./components/SendMessage";
import dataMessages from './assets/data-messages'

export default {
  data () {
    return {
      dataMessages: dataMessages
    }
  },
  name: 'app',
  components: {
    Message,
    Messages,
    SendMessage
  }
}
</script>

<style lang="scss">
  #app {
    margin-top: 60px;
  }
  * {
    box-sizing: border-box;
  }
</style>

<template>
    <div class="add-message">
      <input class="add-message__field" type="text" v-model="customMessage">
      <button class="add-message__send" @click="sendMessage">Отправить</button>
    </div>
</template>

<script>
    export default {
        name: "SendMessage",
        data(){
            return {
                customMessage: null
            }
        },
        props: {
            msgs: Object
        },
        methods: {
            sendMessage: function () {
                this.msgs.messages.push({
                    "message": this.customMessage,
                    "status": "show"
                });
            }
        }
    }
</script>

<style scoped lang="scss">
  .add-message{
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    &__field{
      width: 300px;
      max-width: 100%;
      height: 30px;
      margin-right: 20px;
      border: 2px solid;
    }
    &__send{
      height: 30px;
      width: 200px;
      max-width: 100%;
      border: 2px solid;
    }
  }

</style>

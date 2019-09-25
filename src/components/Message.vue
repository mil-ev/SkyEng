<template>
  <div class="current-message">
    <div class="current-message__del" @click="delMessage">&#10006;</div>
    <div class="current-message__text">{{msg.message}}</div>
  </div>
</template>

<script>
    export default {
        data() {
            return {
                showMessages: [],
                msg: Object,
                current: 0,
                currentLength: this.msgs.messages.length
            }
        },
        name: 'Message',
        props: {
            msgs: Object
        },
        methods: {
            changeStatus: function(){
                var that = this;

                this.msgs.messages.find(function (currentValue) {
                    if(currentValue === that.msg){
                        currentValue.status = "hide";
                    }
                });
            },
            delMessage: function () {
                this.changeStatus();

                let index = this.showMessages.indexOf(this.msg);

                if (index !== -1){
                    this.showMessages.splice(index, 1);
                    if(this.current > 0) this.current--
                }
            },
            showMessage: function () {
                var that = this;

                that.showMessages =  Array.from(that.msgs.messages);
                that.msg = that.showMessages[that.current];
                setInterval(function () {
                    that.msg = that.showMessages[that.current];
                    that.current++;
                    if (that.current >= that.showMessages.length) that.current = 0
                }, 2000)
            }
        },
        watch:{
                msgs: {
                    immediate: true,
                    deep: true,
                    handler(newMessages) {
                        if(this.currentLength < newMessages.messages.length) {
                            let newItem = newMessages.messages[newMessages.messages.length - 1];
                            this.showMessages.push(newItem);
                            this.currentLength = newMessages.messages.length
                        }
                    }
            }
        },
        created() {
            this.showMessage()
        }
    }
</script>

<style scoped lang="scss">
  .current-message {
    display: flex;
    align-items: center;
    padding: 10px 15px;
    border: 2px solid;

    &__del {
      width: 15px;
      margin-right: 15px;
      cursor: pointer;
    }
  }
</style>

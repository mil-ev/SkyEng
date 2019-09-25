<template>
      <ul class="list-messages">
        <li class="list-messages__item" v-for="msg in msgs.messages" :key="msg.id">
          <div class="list-messages__status">{{msg.status === "show" ? '' : "&#10006"}}</div>
          <div class="list-messages__text">{{msg.message}}</div></li>
      </ul>
</template>

<script>
export default {
  name: 'Messages',
  props: {
    msgs: Object
  }
}
</script>

<style scoped lang="scss">
  .list-messages{
    list-style: none;
    padding: 10px 15px;
    border: 2px solid;
    &__item{
      display: flex;
      align-items: center;
    }
    &__status{
      width: 15px;
      height: 22px;
      margin-right: 15px;
    }
  }

</style>

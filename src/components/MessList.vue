<template>
  <div class="message" v-for="message in messages" :key="message">
    <div class="top">
      <img src="../assets/images/user.png" alt="user icon" class="user-icon">
      <div class="message-body">
        <span class="user-name">{{ message.name }}</span>
        <span class="time">{{ message.time }}</span>
        <p class="body">{{ message.body }}</p>
      </div>
    </div>
    <under-buttons class="buttons" :buttons="buttons"/>
  </div>
</template>

<script>
import UnderButtons from './UnderButtons.vue';
export default {
  props: {
    messages: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      buttons: [
        {id: 1, name: 'Like'},
        {id: 2, name: 'Reply'},
        {id: 3, name: 'More'}
      ]
    }
  },
  components: {
    UnderButtons
  }
}
</script>

<style scoped>
  .top {
    display: flex;
    align-items: start;
  }
  .message {
    margin-bottom: 15px;
    margin-left: 65px;
  }
  .message-body {
    max-width: 500px;
    word-wrap: break-word;
    background-color: rgb(245, 245, 245);
    border-radius: 20px;
    padding: 10px 20px;
  }
  .buttons {
    margin-left: 65px;
    --buttonFontSize: 12px;
  }
  .time {
    margin-left: 5px;
    color: rgb(133, 133, 133);
    font-size: 14px;
  }
</style>
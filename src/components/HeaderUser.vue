<template>
  <div class="header">
    <img src="../assets/images/main.png" alt="main icon" class="user-icon">
    <div class="desc">
      <p class="name">{{header.name}}</p>
      <p class="date">{{header.date}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    header: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .header {
    display: flex;
    align-items: center;
  }
  .name {
    color: blueviolet;
    font-weight: bold;
  }
  .date {
    color: rgb(133, 133, 133);
    font-size: 14px;
    margin-top: 5px;
  }
</style>
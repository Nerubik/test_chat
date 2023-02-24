<template>
  <div class="buttons">
    <div v-for="button in buttons" :key="button">
      <span class="under-button">{{ button.name }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    buttons: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
  .buttons {
    display: flex;
  }
  .under-button {
    color: rgb(133, 133, 133);
    font-size: var(--buttonFontSize, 14px);
    margin-right: 10px;
    cursor: pointer;
  }
  .under-button:hover {
    color: rgb(41, 41, 41);
  }
</style>
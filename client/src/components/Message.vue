<template>
  <div class="message" :class="message.author">
    <div class="message__bubble">
      <p>{{ message.message }}</p>
    </div>
    <div v-if="message.image" class="message__attachment">
      <img :src="message.image" alt="image" />
    </div>
    <p class="message__author">
      {{ message.author === "bot" ? "NMD-Bot" : "You" }}
    </p>
  </div>
</template>

<script>
export default {
  name: "Message",
  props: {
    message: Object
  }
};
</script>

<style lang="scss" scoped>
.message {
  &__bubble {
    padding: 8px 16px;
    border-radius: 16px;
    background: #ededed;
    max-width: 40%;
  }

  &__attachment {
    max-height: 200px;
    max-width: 30%;
    border-radius: 16px;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: contain;
    }
  }

  &__author {
    font-size: 12px;
    color: #565656;
  }

  &.bot {
    text-align: left;

    .message__bubble {
      background: #5f6caf;
      color: #fff;
      border-bottom-left-radius: 0;
    }
  }

  &.client {
    text-align: right;

    .message__bubble {
      background: #f2f2f2;
      color: #232323;
      border-bottom-right-radius: 0;
      margin-left: auto;
      margin-right: 0;
    }
  }
}
</style>

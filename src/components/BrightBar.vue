<template>
  <div class="bright-bar">
    <p>Bright</p>
    <input v-model="bright" type="range" min="0" max="15" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      bright: 10,
    };
  },
  watch: {
    bright() {
      this.bright = this.bright;
      if (this.bright > 2) {
        document.documentElement.style.filter = `brightness(${this.bright /
          10})`;
      }
    },
  },
};
</script>

<style>
.bright-bar {
  color: var(--text-primary-color);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height: 100%;
}
.bright-bar input {
  max-width: 100px;
  height: 23px;
}
</style>

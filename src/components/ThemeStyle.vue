<template>
  <div class="dark-mode-btn">
    <p>Theme</p>
    <input type="checkbox" class="checkbox" id="checkbox" @click="themeSwich" />
    <label for="checkbox" class="label">
      <i class="fas fa-moon"></i>
      <i class="fas fa-sun"></i>
      <div class="ball"></div>
    </label>
  </div>
</template>

<script>
export default {
  methods: {
    themeSwich() {
      document.body.classList.toggle('dark-mode');
    },
  },
};
</script>

<style>
/*
============
DARKMODE
============
 */
.dark-mode-btn {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height: 100%;
  color: var(--text-primary-color);
}
.label {
  background-color: var(--baseColor);
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  border-radius: 50px;
  height: 26px;
  width: 100%;
  padding: 5px;
}
.checkbox {
  display: none;
}
.checkbox:checked + .label .ball {
  transform: translateX(22px);
}
.ball {
  height: 22px;
  width: 20px;
  background: var(--primaryColor);
  position: absolute;
  border-radius: 50%;
  transition: all 0.5s ease;
}
.label i {
  color: #f1c40f;
}
@media screen and (min-width: 678px) {
  .dark-mode-btn {
    margin-right: 2rem;
  }
}
</style>

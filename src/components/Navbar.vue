<template>
  <div class="navbar-container">
    <div id="nav">
      <div class="logo">
        <a target="_blank" href="https://my-portfolio-blog-website.netlify.app/"
          >Maxi Ruti</a
        >
      </div>
      <div class="options">
        <ThemeStyle />
        <BrightBar />
      </div>
    </div>
  </div>
</template>

<script>
import ThemeStyle from './ThemeStyle';
import BrightBar from './BrightBar';
export default {
  components: { ThemeStyle, BrightBar },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.navbar-container {
  background: var(--secundaryColor);
  margin-bottom: 2rem;
  box-shadow: 0 3px 10px var(--primaryColor);
}
#nav,
.links,
.options {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}

#nav {
  padding: 30px;
  justify-content: space-between;
  max-width: 1070px;
  margin: 0 auto;
}
.logo a {
  font-size: 1rem;
  color: var(--text-primary-color);
  font-size: 1.5em;
  font-weight: bold;
  color: var(--text-primary-color);
}
.options {
  height: 60px;
}
.options p {
  font-size: 17px;
}
</style>

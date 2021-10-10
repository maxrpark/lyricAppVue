<template>
  <div class="search-song">
    <div class="search">
      <h2>Search for your favorite song</h2>
      <form class="form" @submit.prevent="getSong">
        <label>Artist</label>
        <input v-model="artist" placeholder="Enter artist" />
        <label>Song</label>
        <input v-model="song" placeholder="Enter song" />
        <button class="btn" type="submit">Get me lyric!</button>
      </form>
    </div>
    <div class="song-container" v-if="lyric.length > 0">
      <div class="song-links">
        <div class="single-link">
          <a target="_blank" class="" :href="listenOnYoutube"
            ><i class="fab fa-youtube icon youtube"></i
            ><small>{{ Song }}</small></a
          >
        </div>
        <div class="single-link">
          <a target="_blank" :href="readOnWikipedia"
            ><i class="fab fa-wikipedia-w icon wiki"></i
            ><small>{{ Title }}</small></a
          >
        </div>
      </div>
      <h2>{{ Title }}</h2>
      <h2>"{{ Song }}"</h2>

      <div class="song-lyric">
        <pre><p>{{ lyric }}</p></pre>
      </div>
    </div>
    <div v-else>
      <h4>{{ error }}</h4>
    </div>
  </div>
</template>

<script>
const axios = require('axios').default;
export default {
  data() {
    return {
      songTitle: '',
      artistName: '',
      lyric: '',
      artist: '',
      song: '',
      error: '',
      noValue: 'Please enter some artist and song name',
    };
  },
  methods: {
    async getSong() {
      try {
        const response = await axios.get(
          `https://api.lyrics.ovh/v1/${this.artist}/${this.song}`
        );
        this.lyric = await response.data.lyrics;
        this.songTitle = this.song;
        this.artistName = this.artist;
        this.artist = '';
        this.song = '';
      } catch (error) {
        this.error = ' No song found with those names';
        this.lyric = '';
      }
    },
  },
  computed: {
    Title() {
      return this.artistName.charAt(0).toUpperCase() + this.artistName.slice(1);
    },
    Song() {
      return this.songTitle.charAt(0).toUpperCase() + this.songTitle.slice(1);
    },
    listenOnYoutube() {
      return `https://www.youtube.com/results?search_query=${this.artistName} ${this.songTitle} lyrics`;
    },
    readOnWikipedia() {
      return `https://wikipedia.org/wiki/${this.artistName}`;
    },
  },
};
</script>

<style scoped>
.search-song {
  color: var(--text-primary-color);
}
.form {
  display: flex;
  flex-direction: column;
  max-width: 600px;
  gap: 10px;
  margin: 1rem;
  background: var(--secundaryColor);
  padding: 1rem;
  border-radius: 5px;
  border: 1px solid var(--baseColor2);
}
input {
  height: 2rem;
  margin: 0 1rem;
  text-align: center;
  font-size: 1.2rem;
}
.btn {
  margin: 1rem 1rem auto 1rem;
  height: 2rem;
  background: #ff7f50;
  border: none;
  position: relative;
  transition: all 0.2s linear;
  border-radius: 5px;
  font-size: 1.2rem;
  color: var(--secundaryColor);
}

.btn:hover {
  background: hsla(16, 100%, 66%, 0.8);
  color: var(--text-primary-color);
}

.song-container {
  margin: 2rem auto;
  background: var(--secundaryColor);
  margin: 1rem;
  padding: 1rem;
  border-radius: 5px;
  box-shadow: 0 3px 10px rgb(0 0 0 / 0.2);
}
.song-container h2 {
  margin: 1rem;
}
.song-lyric {
  margin: 25px;
}
.song-lyric p {
  font-size: 1.2rem;
}
pre {
  white-space: pre-wrap;
}
.song-links {
  display: flex;
  gap: 1rem;
  justify-content: center;
  align-items: center;
}
.single-link {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 200px;
}
.icon {
  font-size: 2rem;
}
.wiki {
  color: var(--text-primary-color);
}
.youtube {
  color: red;
}
a {
  display: flex;
  flex-direction: column;
  color: var(--text-primary-color);
  font-size: 1.2rem;
}
@media screen and (min-width: 700px) {
  .form,
  .song-container {
    margin: 1rem auto;
    max-width: 600px;
  }
}
</style>

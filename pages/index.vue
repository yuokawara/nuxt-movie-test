<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        movie-test
      </h1>
      <div class="player-container">
        <vue-core-video-player src="https://www9.nhk.or.jp/das/movie/D0002160/D0002160619_00000_V_000.mp4"></vue-core-video-player>
        <ul>
      <li v-for="profile in ListItems" :key="profile.name">
        {{ profile.value }}
      </li>
      </ul>
        <button v-if="(ListItems.length - count) >= 0" type="button" @click="isMore">test</button>
      </div>
    </div>
  </div>
</template>

<script>
import sampleJson from '~/static/profile.json'

export default {
  data() {
    return {
      profile: sampleJson.profile,
      count: 1,
    }
  },
  computed: {
    ListItems() {
      const list = this.profile
      return list.slice(0, this.count)
    }
  },
  methods: {
    isMore() {
      this.count += 1
    },
  },
}

</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.player-container {
  width: 720px;
  height: 480px;
}

.player-container button {
  padding: 10px;
  margin: 10px;
}

</style>

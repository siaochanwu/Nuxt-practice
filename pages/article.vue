<template>
  <section class="">
    <div v-for="item in articles" :key="item.id">
      <p>{{ item.title }}</p>
      <a :href="item.url">
        <p>{{item.url}}</p>
        <!-- <img :src="item.media[0]['media-metadata'].url" alt> -->
      </a>
      <p>{{ item.updated }}</p>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      articles: '你看不到這篇新聞'
    }
  },
  asyncData({ $axios }) {
    const url = 'https://api.nytimes.com/svc/mostpopular/v2/viewed/1.json?api-key=0zGOQYz5arpHSsBUnvP4kaW2iVrkHVGS';
    return $axios.get(url).then(res => {
      console.log(res.data)
        return { articles: res.data.results }
    })
  }
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

.links {
  padding-top: 15px;
}
</style>

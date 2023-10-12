<template>
  <div id="app">
    <TheHeader />

    <main class="container">
      <TheHero />

      <div class="row mb-2">
        <Article v-for="(article, index) in articles" :key="index" :article="article" />
      </div>
    </main>

  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader.vue'
import TheHero from '@/components/TheHero.vue'
import Article from '@/components/CardArticle.vue'

export default {
  components: {
    TheHeader,
    TheHero,
    Article
  },
  data () {
    return {
      articles: []
    }
  },
  async fetch () {
    await this.$axios.$get('v1/cnn-news')
      .then((res) => { this.articles = res.data })
  },
  mounted () {
    console.log('Artikel: ', this.articles)
  }
}
</script>
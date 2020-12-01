<template lang="pug">
section
  .text-h2.font-weight-medium.white--text.hidden-sm-and-down.text-center.text-capitalize {{ about.title }}
  v-row(justify='end', no-gutters)
    v-col(cols='12', md='6')
      v-container
        .text-h2.hidden-md-and-up.text-center.mb-6.blue-grey--text {{ about.title }}
        p.pa-md-6.rounded-lg {{ about.content }}
    v-col.hidden-md-and-up(order='first')
      v-img(:src='about.img')
</template>

<script>
export default {
  layout: 'main',
  async asyncData({ $content }) {
    const about = await $content('pages/about').fetch()

    return { about }
  },
}
</script>

<style lang="sass" scoped>
@media (min-width: 960px)
  section
    background-image: url('https://res.cloudinary.com/seabothsides/image/upload/v1606484206/wingsBheki/about_dysnpa.svg')
    background-size: 100%
    height: 100vh
  p
    color: white
    background-color: #005EB83f
    margin: 20% 0
</style>

<template lang="pug">
v-row(no-gutters, align='center')
  v-col
    v-img(:src='apply.img')
  v-col.text-center(cols='12', md='6')
    v-container
      p.text-h2.text-capitalize.blue-grey--text.mt-5 {{ apply.title }}
      p {{ apply.content }}
  v-col.text-center(cols='12', md='6')
    h3.secondary--text.ma-5 Please use this button to download a copy of our application form
    v-btn.v-btn--contained.primary.mt-2(
      icon,
      fab,
      x-large,
      color='white',
      target='_blank',
      :to='apply.pdf',
      download
    )
      v-icon mdi-file-pdf
</template>

<script>
export default {
  layout: 'main',
  async asyncData({ $content }) {
    const apply = await $content('pages/apply').fetch()

    return { apply }
  },
}
</script>

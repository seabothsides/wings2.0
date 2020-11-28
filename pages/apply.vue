<template lang="pug">
v-row(no-gutters)
  v-col
    v-img(:src='apply.img')
  v-col.text-center(cols='12')
    p.pt-8.px-5.px-md-16 {{ apply.content }}
  v-col.text-center
    .mb-md-8
      h3.secondary--text.mx-5 Please use this button to download a copy of our application form
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

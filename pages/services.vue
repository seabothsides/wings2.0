<template lang="pug">
v-container.mb-10
  p.text-center {{ services.title }}
  v-row
    v-col(
      v-for='(i, index) in services.services.title',
      :key='index',
      cols='12',
      md='6'
    )
      v-card.mb-sm-8.pa-5.mx-sm-auto(max-width='550')
        v-row
          v-col.text-center(cols='12')
            v-expansion-panels(flat)
              v-expansion-panel
                v-expansion-panel-header.justify-center(hide-actions) {{ services.services.title[index] }}
                v-expansion-panel-content.text-justify {{ services.services.content[index] }}
          v-col(cols='12', order='first', justify='center')
            v-img.mx-auto(
              :src='services.services.img[index]',
              max-height='230',
              contain
            )
</template>

<script>
export default {
  layout: 'main',
  async asyncData({ $content }) {
    const services = await $content('pages/services').fetch()

    return { services }
  },
}
</script>

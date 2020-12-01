<template lang="pug">
v-container.mb-10
  p.text-center.text-h2.text-capitalize.blue-grey--text {{ services.title }}
  v-row
    v-col(
      v-for='(i, index) in services.services.title',
      :key='index',
      cols='12',
      md='6'
    )
      v-card.mb-sm-8.pa-5.mx-sm-auto(max-width='550', color='#f8f8f8')
        v-row
          v-col.text-center(cols='12')
            v-expansion-panels(flat, inset)
              v-expansion-panel
                v-expansion-panel-header.justify-center(
                  hide-actions,
                  color='light-blue lighten-1'
                ) 
                  p.text-center.title.mb-n1.text-capitalize {{ services.services.title[index] }}
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

<style lang="sass" scoped>
.v-expansion-panel
  .v-expansion-panel-header
    color: #fff !important
</style>

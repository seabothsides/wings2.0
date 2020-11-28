<template lang="pug">
v-container(fluid, fill-height)
  v-row
    v-col(cols=12, align='center')
      h1 {{ landing.title }}
      v-layout(align-center, justify-center)
        v-sheet(height='75vh')
        v-row
          v-col(cols=12, md=6)
            p.text-h3.font-weight-black {{ landing.apply.content }}
            p.overline Download our application form to the right
          v-col(cols=12, md=6)
            v-btn.v-btn--contained.primary.mt-2(
              icon,
              fab,
              x-large,
              color='white',
              target='_blank',
              nuxt,
              :to='landing.apply.pdf',
              download
            )
              v-icon mdi-file-pdf
    v-col(cols=12, align='center')
      v-btn(text, to='services', color='secondary') {{ landing.services.cta }}
      v-layout(align-center, justify-center)
        v-sheet(height='40vh')
        v-row(dense)
          v-col(
            v-for='(i, index) in landing.services.title',
            :key='index',
            cols=12,
            md=3,
            align='center',
            justify='center'
          )
            v-card.d-md-inline-block.pa-2.mx-2(
              tile,
              width='80%',
              height='100%'
            )
              h3.text-center {{ landing.services.title[index] }}
              v-avatar(size='62', tile)
                v-img.justify-center(
                  :src='landing.services.img[index]',
                  contain
                )
    v-col(cols=12, align='center')
      v-layout(align-center, justify-center)
        v-sheet(height='50vh')
        v-row
          v-col(cols=12)
            p.text-capitalize.text-h5.font-weight-medium {{ landing.contact.cta }}
          v-col(cols=12, md=6)
            p.font-weight-bold.text-h6 Email: {{ landing.contact.email }}
          v-col(cols=12, md=6)
            p.font-weight-bold.text-h6 Mobile: {{ landing.contact.phone }}
          v-col(cols=12)
            v-btn(text, x-large, to='about', color='primary') read more now
</template>

<script>
export default {
  async asyncData({ $content }) {
    const landing = await $content('index').fetch()

    return { landing }
  },
  data() {
    return {}
  },
  head() {
    return {
      title: this.landing.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.landing.description,
        },
        // Open Graph
        { hid: 'og:title', property: 'og:title', content: this.landing.title },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.landing.description,
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.landing.title,
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.landing.description,
        },
      ],
    }
  },
}
</script>

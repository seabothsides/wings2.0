<template lang="pug">
v-container(fluid, fill-height)
  v-row
    v-col(cols=12, align='center')
      h1.text-capitalize.blue-grey--text {{ landing.title }}
      v-layout(align-center, justify-center)
        v-sheet(height='75vh')
        v-row
          v-col(cols=12, md=6)
            p.text-h3.font-weight-black
              nuxt-link(to='apply', style='text-decoration: none') {{ landing.apply.content }}
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
      v-btn.mb-6(to='services', color='secondary', x-large) {{ landing.services.cta }}
      v-layout(align-center, justify-center)
        v-sheet(height='40vh')
        v-row
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
              height='100%',
              color='#f8f8f8'
            )
              h3.text-center {{ landing.services.title[index] }}
              v-avatar(size='62', tile)
                v-img.justify-center(
                  :src='landing.services.img[index]',
                  contain
                )
    v-col(cols=12, align='center')
      v-layout(align-center, justify-center)
        v-sheet(height='40vh')
        v-row
          v-col(cols=12)
            p.text-capitalize.text-h5.font-weight-medium.blue-grey--text {{ landing.contact.cta }}
          v-col(cols=12, md=6)
            p.font-weight-bold.text-h6
              a(:href='`mailto:${landing.contact.email}`', target='_blank') {{ landing.contact.email }}
          v-col(cols=12, md=6)
            p.font-weight-bold.text-h6 
              a(:href='`tel:${landing.contact.phone}`') {{ landing.contact.phone }}
          v-col(cols=12)
            v-btn(x-large, to='about', color='primary') read more now
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

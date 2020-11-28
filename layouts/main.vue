<template lang="pug">
v-app
  v-app-bar(app, color='light-blue lighten-1')
    nuxt-link(to='/')
      v-img.my-10(
        contain,
        position='left center',
        height='55',
        src='https://res.cloudinary.com/seabothsides/image/upload/v1606484206/wingsBheki/wingslogo_c6gy0x.svg'
      )
    v-toolbar-title.hidden-xs-only.white--text Wings Health Care
    v-spacer
    .hidden-sm-and-down
      v-btn.ml-4.white--text(
        v-for='i in pages',
        :key='i',
        :to='i',
        exact,
        active-class='secondary',
        text
      ) {{ i }}
    .hidden-md-and-up 
      v-menu(offset-y, left, min-width='15', transition='slide-y-transition')
        template(v-slot:activator='{ on, attrs }')
          v-btn.white--text(text, color='white', v-bind='attrs', v-on='on') site nav
        v-list
          v-list-item.text-capitalize.white--text(
            v-for='i in pages',
            :key='i',
            :to='i',
            exact,
            active-class='secondary',
            color='white'
          ) {{ i }}
  v-main.bluealt1
    nuxt
</template>

<script>
export default {
  data() {
    return {
      pages: ['about', 'services', 'apply', 'contact'],
    }
  },
}
</script>

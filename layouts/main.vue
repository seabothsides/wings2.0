<template lang="pug">
v-app
  v-app-bar(app)
    nuxt-link(to='/')
      v-img.my-10(
        contain,
        position='left center',
        height='55',
        src='https://res.cloudinary.com/seabothsides/image/upload/v1606484206/wingsBheki/wingslogo_c6gy0x.svg'
      )
    v-toolbar-title.hidden-xs-only Wings Health Care
    v-spacer
    .hidden-sm-and-down
      v-btn.ml-4(to='about') About
      v-btn.ml-4(to='services') services
      v-btn.ml-4(to='apply') apply
      v-btn.ml-4(to='contact') contact
    .hidden-md-and-up 
      v-menu(offset-y, left, min-width='15', transition='slide-y-transition')
        template(v-slot:activator='{ on, attrs }')
          v-btn(text, color='white', v-bind='attrs', v-on='on') site nav
        v-list
          v-list-item(to='/about') About
          v-list-item(to='/services') Services
          v-list-item(to='/apply') Apply
          v-list-item(to='/contact') Contact
  v-main
    nuxt
</template>

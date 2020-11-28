<template lang="pug">
v-row.mb-10(no-gutters, align='center')
  v-col
    v-img(:src='contact.img', max-height='370', fill)
  v-col(cols='12', md='6')
    p.pa-5 {{ contact.content }}
  v-col(cols='12', md='6')
    form.px-8.mx-md-8.px-md-8.my-md-8(
      ref='form',
      method='post',
      name='contact-form',
      data-netlify='true',
      data-netlify-honeypot='bot-field'
    )
      input(type='hidden', name='form-name', value='contact-form')/
      v-row(justify='center')
        v-col(cols='12', sm='6')
          v-text-field(
            name='email',
            prepend-inner-icon='mdi-email',
            label='E-mail',
            required
          )
        v-col(cols='12', sm='6')
          v-text-field(
            name='name',
            prepend-inner-icon='mdi-account',
            label='Name',
            required
          )
        v-col(cols='12')
          v-text-field(
            name='subject',
            prepend-inner-icon='mdi-pen',
            label='Subject',
            required
          )
        v-col(cols='12')
          v-textarea(
            name='message',
            outlined,
            prepend-inner-icon='mdi-android-messages',
            label='message',
            required
          )
        v-btn(
          @='validate',
          type='submit',
          max-width='min-content',
          large,
          rounded,
          color='secondary'
        ) Send Message
</template>

<script>
export default {
  layout: 'main',
  async asyncData({ $content }) {
    const contact = await $content('pages/contact').fetch()

    return { contact }
  },
  methods: {
    validate() {
      this.$refs.form.validate()
    },
  },
}
</script>

<style lang="sass" scoped></style>

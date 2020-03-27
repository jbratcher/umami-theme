<template>
  <v-container class="pa-0" fluid>
    <v-row>
      <v-col class="py-0">
        <v-card class="d-flex flex-column mx-auto text-center pt-9 pb-12">
          <!-- Content Section -->
          <v-container class="d-none">
            <h1>Contact</h1>
          </v-container>

          <v-container>
            <h2
              :class="{'display-2 mb-3': $breakpoint.mdAndUp, 'display-1 mb-3': $breakpoint.smAndDown}"
            >Have a question?</h2>
            <p>Send us a message!</p>
          </v-container>

          <v-form
            class="px-12"
            id="contact-form"
            ref="form"
            v-model="valid"
            name="contact"
            method="post"
            value="contactform"
            data-netlify="true"
            data-netlify-honeypot="bot-field"
            lazy-validation
          >
            <input type="hidden" name="form-name" value="contact" />
            <v-text-field v-model="name" :rules="nameRules" label="Name" name="name" required></v-text-field>
            <v-text-field v-model="email" :rules="emailRules" label="E-mail" name="email" required></v-text-field>
            <v-textarea
              v-model="message"
              :rules="messageRules"
              label="Your Message"
              name="message"
              required
            ></v-textarea>
            <v-btn class="mr-4" name="reset" color="info" @click="reset">Reset</v-btn>
            <v-btn
              type="submit"
              name="submit"
              :disabled="!valid"
              color="primary"
              class="mr-4"
            >Submit</v-btn>
          </v-form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Contact',
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }
      ]
    }
  },
  data: () => ({
    sliderModel: null,
    valid: true,
    name: '',
    nameRules: [v => !!v || 'Name is required'],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid'
    ],
    message: '',
    messageRules: [
      v => !!v || 'Message is required',
      v =>
        (v && v.length <= 1000) ||
        'Your message must be less than 1000 characters. Please email us at company@email.com'
    ]
  }),
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.snackbar = true
      }
    },
    reset() {
      this.$refs.form.reset()
      this.$refs.form.resetValidation()
    }
  }
}
</script>

<style lang="scss">
</style>

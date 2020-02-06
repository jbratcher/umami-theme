<template>
  <v-layout>
    <v-row>
      <v-col class="py-12">
        <main id="contact-page">
          <v-sheet>
            <!-- Content Section -->
            <section hidden>
              <h1>Contact</h1>
            </section>

            <section class="content-container">
              <h2>Have a question?</h2>
              <p>Send us a message!</p>
            </section>

            <v-form
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
              <v-text-field
                v-model="email"
                :rules="emailRules"
                label="E-mail"
                name="email"
                required
              ></v-text-field>
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
                color="secondary"
                class="mr-4"
              >Submit</v-btn>
            </v-form>
          </v-sheet>
        </main>
      </v-col>
    </v-row>
  </v-layout>
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
#contact-page {
  text-align: center;
  & > section {
    margin-bottom: 4rem;
  }
  h2 {
    font-size: 2rem;
  }
  p {
    font-size: 1.5rem;
  }
  .v-form {
    max-width: 75vw;
    margin: 0 auto;
    padding: 2rem 0;
    text-align: right;
  }
}

@media screen and (min-width: 960px) {
  #contact-page {
    & > section {
      margin-bottom: 4rem;
    }
    .v-form {
      max-width: 50vw;
    }
  }
}
</style>

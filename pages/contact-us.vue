<template>
  <div class="contact-us">
    <div v-if="formSubmitted" class="submitted">
      <p>Thank you.</p>
      <p>Your enquiry has been submitted.</p>
    </div>
    <form v-else>
      <div class="group g1">
        <label for="name">Name</label>
        <input id="name" v-model="info.name" type="text" />
      </div>
      <div class="group g1">
        <label for="email">Email</label>
        <input id="email" v-model="info.email" type="text" />
      </div>
      <div class="group g2">
        <label for="message">Message</label>
        <textarea
          id="message"
          v-model="info.message"
          cols="30"
          rows="10"
        ></textarea>
      </div>
      <div class="antispam">
        <antispam
          v-if="result == 'unverified'"
          result="unverified"
          @updateResult="result = arguments[0]"
        />
      </div>
      <div class="group actions center">
        <button @click.prevent="clear">Clear</button>
        <button v-if="result == 'verified'" @click.prevent="validate">
          Submit
        </button>
        <button v-else class="disabled" @click.prevent>Submit</button>
      </div>
      <div class="error">{{ formResult }}</div>
    </form>
    &nbsp;
  </div>
</template>

<script>
// import SendIcon from 'vue-material-design-icons/EmailSend.vue'
// import DeleteIcon from 'vue-material-design-icons/TrashCanOutline.vue'
// import antispam from '~/components/antispam'
export default {
  layout: 'blue',
  data() {
    return {
      info: {
        name: '',
        email: '',
        message: '',
        submitToOskars: true,
      },
      size: 40,
      result: 'unverified',
      formSubmitted: false,
      formResult: '',
    }
  },
  head: {
    title: 'Contact Us | Bangkok Pavilion',
    meta: [
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      {
        hid: 'description',
        name: 'description',
        content: 'Contact us by sending us an email',
      },
    ],
  },
  methods: {
    clear() {
      this.info.name = ''
      this.info.email = ''
      this.info.message = ''
      this.formResult = ''
    },
    validate() {
      this.formResult = ''
      const _ = this.info
      const re =
        /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      let err = false
      let emailErr = ''
      if (_.name === '' || _.email === '' || _.message === '') err = true
      if (_.email.trim() !== '') {
        if (re.test(String(this.info.email).toLowerCase()) === false) {
          err = true
          emailErr = ' and email needs a valid format'
        }
      } else {
        err = true
      }
      if (err === true) this.formResult = 'pls fill in all fields' + emailErr
      if (err === false) this.submit()
    },
    submit() {
      this.$axios
        .post('https://bangkokpavilion.co.uk/mailer2.php', this.info)
        .then((res) => {
          if (res.data === 'Success') {
            this.formSubmitted = true
          } else {
            console.log(res.data)
            this.formResult =
              'Sorry your message was not sent. Please try again later.'
          }
        })
    },
  },
}
</script>

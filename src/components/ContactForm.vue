<template>
  <div class="container">
      <div>
        <label>Name</label>
        <input 
          type="text" 
          v-model="name"
          name="name"
          placeholder="Your Name"
        >
        <label>Email</label>
        <input 
          type="email" 
          v-model="email"
          name="email"
          placeholder="Your Email"
          >
        <label>Message</label>
        <textarea 
          name="message"
          v-model="message"
          cols="30" rows="5"
          placeholder="Message">
        </textarea>
        <div @click="sendEmail">Submit</div>
<!--         
        <input type="submit" value="Send"> -->
      </div>
  </div>
</template>
<script>
import emailjs from 'emailjs-com';
export default {
  name: 'ContactUs',
  data() {
    return {
      name: '',
      email: '',
      message: ''
    }
  },
  methods: {
    // sendEmail() {
    //   console.log('sendEmail')
    //   try {
    //     emailjs.sendForm('service_ge0dtua', 'template_c8m06d9', ``)

    //   } catch(error) {
    //       console.log({error})
    //   }
    //   // Reset form field
    //   this.name = ''
    //   this.email = ''
    //   this.message = ''
    // },
    sendEmail() {
      const templateParams = {
        from_name: this.name,
        from_email: this.email,
        message: this.message
      };

      emailjs.send(
        'service_ge0dtua',
        'template_c8m06d9',
        templateParams,
        'UmMIsqIGcJY0y6uUO'
      )
      .then((response) => {
        console.log('Email sent successfully!', response.status, response.text);
      }, (error) => {
        console.log('Email failed to send:', error);
      });
    }
  }
}
</script>

<style scoped>
* {box-sizing: border-box;}

.container {
  display: block;
  margin:auto;
  text-align: center;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  width: 50%;
}

label {
  float: left;
}

input[type=text], [type=email], textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type=submit] {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}
</style>
<template>
  <div id="home">
    <contact-form></contact-form>
  </div>
</template>

<script>
import ContactForm from '@/components/ContactForm.vue'

export default {
  name: "HomeView",
  components: {
    ContactForm
  }
}
</script>
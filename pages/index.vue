<template>
  <div class="container text-center mt-5">
    <div>
      <logo />
      <h1 class="title mt-5">
        Kita Siapaaaa!!!
      </h1>
      <h2 class="subtitle">
        Project Mantab-Mantab Nyoyy
      </h2>
      <div class="links mt-5">
        <b-btn variant="success" href="https://digitalregs.com" target="_blank">
          Web
        </b-btn>
        <b-btn
          variant="secondary"
          href="https://github.com/regasyahfika"
          target="_blank"
        >
          GitHub
        </b-btn>
        <b-btn
          variant="primary"
          href="https://www.linkedin.com/in/regasyahfika"
          target="_blank"
          >Linkedin</b-btn
        >
      </div>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  }
}
</script>

<template>
  <card title="Getting Started" :no-padding="true">
    <p>
      Embed this script inside <code>body</code> of every page on your
      website to start collecting data.
    </p>
    <pre v-html="script"></pre>
  </card>
</template>

<script>
  import Card from "./Card.vue";

  const trackURI = `${window.location.host}${window.location.pathname}track.js`;
  const script = `
&lt;script>
  (function(n, e, m, E, a, $) {
    n[E]=n[E]||function(){(n[E].q=n[E].q||[]).push(arguments)};$=e.createElement(m);
    $.id=E;$.src=a;$.async=1;m=e.getElementsByTagName(m)[0];m.parentNode.insertBefore($,m)
  })(window, document, "script", "nemea", "https://${trackURI}");

  nemea("view");
&lt;/script>
  `.trim();

  export default {
    components: {Card},

    data() {
      return { script };
    }
  };
</script>

<style lang="scss">
  @import "../../css/_colors.scss";

  .content {
    padding: 1rem;
  }

  p {
    padding: 1rem;
  }

  pre {
    background: $shadow;
    border-radius: 0 0 4px 4px;
    padding: 1rem;
  }
</style>

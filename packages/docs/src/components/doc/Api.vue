<template>
  <div>
    <base-heading>{{ computedHeading }}</base-heading>

    <base-markdown>Generic.Pages.apiText</base-markdown>

    <doc-api-items
      :lang="lang"
      :value="value"
    />
  </div>
</template>

<script>
  // Utilities
  import {
    get,
  } from 'vuex-pathify'

  export default {
    name: 'DocApi',

    props: {
      lang: {
        type: String,
        default: '',
      },
      value: {
        type: Array,
        default: () => ([]),
      },
    },

    computed: {
      ...get('documentation', ['namespace', 'page']),
      computedHeading () {
        const title = `${this.namespace}.${this.page}.apiHeading`

        return this.$te(title) ? 'apiHeading' : 'Generic.Pages.api'
      },
    },
  }
</script>

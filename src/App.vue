<template>
  <v-app>
    <v-main>
      <DevToEmbed userName="venatus"/>
    </v-main>
  </v-app>
</template>

<script>
import DevToEmbed from './components/DevToEmbed';

export default {
  name: 'App',

  components: {
    DevToEmbed
  },

  data: () => ({
    //
  }),
};
</script>

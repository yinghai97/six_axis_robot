<template>

    <v-main>
      <HelloWorld/>
    </v-main>

</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    ipAddress:"",
    ipDialog:false,
    //
  }),
};
</script>

<template>
  <v-app>
    <v-content>
          <ChartOfAccounts />
    </v-content>
  </v-app>
</template>

<script>
import ChartOfAccounts from './components/ChartOfAccounts';


export default {
  name: 'App',

  components: {
    ChartOfAccounts
  },

  data: () => ({
    // add all javascript data 
  }),
};
</script>

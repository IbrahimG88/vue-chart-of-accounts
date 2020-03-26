<template>
  <div>
     
      <!-- Add form and its inputs-->
    <input v-model="Account.name" placeholder="name">
    <p>name is:{{ Account.name }}</p>
    <input v-model="Account.type" placeholder="type">
    <p>Type is: {{ Account.type }}</p>
    <textarea v-model="Account.description" placeholder="description"></textarea>
    <p>Description is: {{ Account.description }}</p>
    <button @click="consoleData">submit</button>
  </div>
</template>

<script>
export default {
    name: 'ChartOfAccounts',
    data: () => ({
    // add all javascript data
    Account:{
    name: '',
    type: '',
    description: ''
    },
    Accounts:[],
    AccountTypes:[]
    }),
    methods:{
        consoleData () {
            console.log(this.Account);
            //this.Account.name = '';
            //this.Account.type = '';
            //this.Account.description = '';
            this.Accounts.push(this.Account);

            if(this.AccountTypes.indexOf(this.Account.type) === -1) {
                this.AccountTypes.push(this.Account.type);
                console.log(this.AccountTypes);
    }
        }
    }
    };
</script>

<style>

</style>
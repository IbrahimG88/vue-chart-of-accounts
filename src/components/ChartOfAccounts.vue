<template>
  <div>
    <v-form ref="form" class="form">
      <v-text-field
        v-model="Account.name"
        :counter="20"
        label="Name"
        required
      ></v-text-field>


      <v-text-field
        v-model="Account.type"
        label="type"
        required
      ></v-text-field>

      <v-text-field
        v-model="Account.description"
        label="description"
        required
      ></v-text-field>


     

      <v-btn
        color="success"
        class="mr-4"
        @click="consoleData"
      >
        Add account
      </v-btn>
    </v-form>
 
    <v-simple-table fixed-header height="300px">
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">Name</th>
            <th class="text-left">Type</th>
            <th class="text-left">Description</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="account in Accounts" :key="account.name">
            <td>{{ account.name }}</td>
            <td>{{ account.type }}</td>
            <td>{{ account.description}}</td>
            <td>
             <i @click="deleteAccount(account.name)" class="fas fa-trash-alt"></i>
             </td>
            
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
export default {
  name: "ChartOfAccounts",
  data() {
    return {
      show: false,
      Account: {
        name: "",
        type: "",
        description: ""
      },
      Accounts: [],
      AccountTypes: []
    };
  },
  methods: {
    consoleData(e) {
      e.preventDefault();
      console.log(this.Account);

      let Account = {
        name: this.Account.name,
        type: this.Account.type,
        description: this.Account.description
      };

      this.Accounts.push(Account);
      this.Accounts.sort((a, b) => (a.type > b.type) ? 1 : -1);

      if (this.AccountTypes.indexOf(this.Account.type) === -1) {
        this.AccountTypes.push(this.Account.type);
        console.log(this.AccountTypes);
      }

      this.Account.name = "";
      this.Account.type = "";
      this.Account.description = "";

    },
    deleteAccount(accountName) {
      this.Accounts = this.Accounts.filter(todo => todo.name !== accountName)
    }
  }
};
</script>

<style scoped>
.form {
  width: 400px;
  margin-left: 30px;
}
</style>
<template>
  <div>
    <form id="add-account" @submit="consoleData">
      <input v-model="Account.name" placeholder="name" />
      <p>name is:{{ Account.name }}</p>
      <input v-model="Account.type" placeholder="type" />
      <p>Type is: {{ Account.type }}</p>
      <textarea v-model="Account.description" placeholder="description"></textarea>
      <p>Description is: {{ Account.description }}</p>
      <input type="submit" value="Submit" />
    </form>
    <div>
    <ul>
      <button @click="toggleShow">toggleshow</button>
      <li v-bind:key="account.name" v-for="account in Accounts">
        {{ account.type }}
        <div>
        {{ show == 1 ?  null: account.description }}
        </div>
      </li>
    </ul>
    </div>
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

      if (this.AccountTypes.indexOf(this.Account.type) === -1) {
        this.AccountTypes.push(this.Account.type);
        console.log(this.AccountTypes);
      }

      this.Account.name = "";
      this.Account.type = "";
      this.Account.description = "";
    },
    toggleShow () {
      this.show = !this.show;
    }
  }
};
</script>

<style>
</style>
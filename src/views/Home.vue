<template>
  <section>
    <h1 class="page-title">List</h1>
    <div class="users-list">
      <UserItem
        v-for="(user, index) in users"
        :key="index"
        :userInfo="user"
        @removeUser="removeUser($event)"
      ></UserItem>
    </div>
  </section>
</template>
<script>
import UserItem from "@/components/UserItem.vue";

export default {
  components: {
    UserItem,
  },
  data: () => ({
    users: [],
    usersListUrl: "https://jsonplaceholder.typicode.com/users",
  }),
  methods: {
    getUserList() {
      fetch(this.usersListUrl, {})
        .then((response) => response.json())
        .then((data) => (this.users = data.slice(0, 5)));
    },
    removeUser(userId) {
      for (let i = this.users.length; i--; ) {
        if (this.users[i].id === userId && this.users.length > 1) {
          this.users.splice(i, 1);
        }
      }
    },
  },
  mounted() {
    this.getUserList();
    if(localStorage.user){
      localStorage.removeItem('user')
    }
  },
};
</script>

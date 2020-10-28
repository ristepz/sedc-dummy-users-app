<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12">
        <h4 class="page-title display-4">Dummy Users App</h4>
      </div>
    </div>
    <div class="row main-row">
      <UserForm :col="userFormCol" @user-created="updateUserList"/>
      <UserList :col="userListCol" :user-list="userList" @set-details="setDetails"/>
      <UserCard :user-details="userDetails" @close-details="closeDetails"/>
    </div>
  </div>
</template>

<script>
import UserForm from "./components/UserForm.vue";
import UserList from "./components/UserList.vue";
import UserCard from "./components/UserCard.vue";

export default {
  name: 'App',
  data() {
    return {
      userList: [],
      userDetails: null,
      userFormCol: 6,
      userListCol: 6,
    };
  },
  created() {
    const users = localStorage.getItem('users');
    if (users) {
      this.userList = JSON.parse(users);
    }
  },
  methods: {
    updateUserList(list) {
      this.userList = list;
    },
    setDetails(user) {
      this.userDetails = user;
      if (user) {
        this.userFormCol = 3;
        this.userListCol = 4;
      }
    },
    closeDetails() {
      this.userFormCol = 6;
      this.userListCol = 6;
      this.userDetails = null;
    }
  },
  components: {
    UserForm,
    UserList,
    UserCard
  }
}
</script>

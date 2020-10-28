<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12">
        <h4 class="page-title display-4">Dummy Users App</h4>
      </div>
    </div>
    <div class="row main-row">
      <UserForm />
      <UserList />
      <UserCard />
    </div>
  </div>
</template>

<script>
import UserForm from './components/UserForm.vue';
import UserList from './components/UserList.vue';
import UserCard from "./components/UserCard.vue";

export default {
  name: 'App',
  components:{
    UserForm,
    UserList,
    UserCard
  }
}
</script>

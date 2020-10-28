<template>
  <div :class="`col-${col}`">
    <div class="pad">
      <div class="form-group">
        <input type="text" class="form-control" v-model="user.FirstName" placeholder="First Name">
      </div>
      <div class="form-group">
        <input type="text" class="form-control" v-model="user.LastName" placeholder="Last Name"/>
      </div>
      <div class="form-group">
        <input type="text" class="form-control" v-model="user.Email" placeholder="Email"/>
      </div>
      <div class="form-group">
        <input type="text" class="form-control" v-model="user.City" placeholder="City"/>
      </div>
      <div class="form-group">
        <input type="text" class="form-control" v-model="user.Age" placeholder="Age"/>
      </div>
      <div class="avatar-selector clearfix">
        <label clearfix>Choose Avatar</label><br/>
        <img v-for="i in 8"
             :key="i"
             :src="`${avatar_url}av${i}.png`"
             @click="setAvatarImage(i)"
             :class="{'active-avatar': selectedAvatar === i}"/>
      </div><br />
      <div class="form-group">
        <button class="btn btn-outline-primary" @click="createUser">Create User</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserForm",
  data() {
    return {
      selectedAvatar: -1,
      avatar_url: `http://localhost:3000/avatars/`,
      user: {
        ID: 0,
        FirstName: '',
        LastName: '',
        Email: '',
        City: '',
        Age: '',
        Avatar: ''
      }
    };
  },
  props:{
    col: {
      type: Number,
      default: 3
    }
  },
  methods:{
    setAvatarImage(index){
      this.selectedAvatar = index;
      this.user.Avatar = index;
    },
    createUser(){
      this.user.ID = `user-${new Date().getTime()}`;
      const users = localStorage.getItem('users');
      let parsedUsers = [];
      if(!users){
        parsedUsers = [this.user];
        localStorage.setItem('users', JSON.stringify(parsedUsers));
      } else {
        parsedUsers = JSON.parse(users);
        parsedUsers.push(this.user);
        localStorage.setItem('users', JSON.stringify(parsedUsers));
      }
      this.$emit('user-created', parsedUsers);
      this.user = {
        ID: 0,
        FirstName: '',
        LastName: '',
        Email: '',
        City: '',
        Age: '',
        Avatar: ''
      };
      this.selectedAvatar = -1;
    }
  }
}
</script>

<style scoped>
div.avatar-selector img {
  max-width: 90px;
  height: auto;
  display: block;
  float: left;
  box-sizing: border-box;
  margin: 5px;
  padding: 4px;
  cursor: pointer;
  border-radius: 4px;
  border: 1px #CCC solid;
}

div.avatar-selector img:hover {
  background: #eaeaea;
}

div.avatar-selector img.active-avatar{
  background: #eaeaea !important;
}
</style>
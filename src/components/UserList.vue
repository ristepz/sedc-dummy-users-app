<template>
  <div :class="[`col-${col}`]">
    <div class="pad">
      <ul class="list-group">
        <li class="list-group-item"
            v-for="(u, i) in this.userList"
            @click="loadDetails(u)"
            :key="i">
          <img :src="`http://localhost:3000/avatars/av${u.Avatar}.png`" width="30" />
          {{ u.FirstName }} {{ u.LastName }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserList",
  data() {
    return {};
  },
  props: {
    userList: {
      type: Array,
      required: true
    },
    col: {
      type: Number,
      default: 4
    }
  },
  methods: {
    loadDetails(user) {
      this.$emit('set-details', user);
    }
  }
}
</script>

<style scoped>
li.list-group-item {
  cursor: pointer;
  transition: all 0.5s ease-in-out;
}

li.list-group-item:hover {
  background: #e5e5e5;
}
</style>
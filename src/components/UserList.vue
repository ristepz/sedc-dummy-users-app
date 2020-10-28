<template>
  <div :class="[`col-${col}`]" v-if="userList.length">
    <div class="pad">
      <ul class="list-group">
        <li :class="['list-group-item', {'active': selected === i}]"
            v-for="(u, i) in this.userList"
            @click="loadDetails(u, i)"
            :key="i">
          <img :src="`http://localhost:3000/avatars/av${u.Avatar}.png`" width="30"/>
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
    return {
      selected: -1,
    };
  },
  props: {
    userList: {
      type: Array,
      default: () => []
    },
    col: {
      type: Number,
      default: 4
    }
  },
  methods: {
    loadDetails(user, i) {
      this.$emit('set-details', user);
      this.selected = i;
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
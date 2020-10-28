<template>
  <div class="col-5" v-if="userDetails">
    <div class="pad">
      <div class="card" style="width: 18rem;">
        <img :src="`http://localhost:3000/avatars/av${userDetails.Avatar}.png`" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">User Details</h5>
          <p class="card-text">Available details for this user.</p>
        </div>
        <ul class="list-group list-group-flush">
          <li class="list-group-item">{{ userDetails.FirstName }}</li>
          <li class="list-group-item">{{ userDetails.LastName }}</li>
          <li class="list-group-item">{{ userDetails.Email }}</li>
          <li class="list-group-item">{{ userDetails.City }}</li>
          <li class="list-group-item">{{ userDetails.Age }}</li>
        </ul>
        <div class="card-body">
          <a href="#" class="btn btn-primary" @click.prevent="closeDetails">Close Details</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserCard",
  props: {
    userDetails: {
      type: Object,
      required: true
    }
  },
  methods: {
    closeDetails() {
      this.$emit('close-details')
    }
  }
}
</script>

<style scoped>

</style>
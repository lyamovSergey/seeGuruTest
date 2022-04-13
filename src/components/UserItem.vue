<template>
  <div class="users-list__item">
    <div class="user-info">
      <p class="user-info__name">{{userInfo.name}}</p>
      <p class="user-info__index">#{{userInfo.id}}</p>
      <p class="user-info__city">{{userInfo.address.city}}</p>
    </div>
    <span class="btn" @click="goTodetail()">View</span>
    <span class="btn btn_light-grey" @click="removeUser(userInfo.id)">Delete</span>
  </div>
</template>
<script>
export default {
  props: ['userInfo'],
  methods: {
    removeUser(id){
      this.$emit('removeUser', id);
    },
    goTodetail(){
      localStorage.setItem('user', JSON.stringify(this.userInfo));
      this.$router.push({ name: 'Details' })
    }
  }
}
</script>
<template>
  <div class="user">
    <p class="user__name">{{ user.name }}</p>
    <span class="user__text user__text_small spacer">id: {{ user.id }}</span>
    <span class="user__text user__text_small spacer">username: {{ user.username }}</span>
    <span class="user__text user__text_small">email: {{ user.email }}</span>
    <p class="user__sub-title">Address</p>
    <p class="user__text">
      {{ user.address.zipcode }} {{ user.address.city }},
      {{ user.address.street }}, {{ user.address.suite }}
    </p>
    <p class="user__text">
      Geo:
      <span class="user__text user__text_small">lat "{{ user.address.geo.lat }}" - lng "{{user.address.geo.lng}}"</span>
    </p>
    <p class="user__sub-title">Phone</p>
    <p class="user__text">{{ user.phone }}</p>
    <p class="user__sub-title">Website</p>
    <a :href="webLink" class="user__text" target="_blank">{{
      user.website
    }}</a>
    <p class="user__sub-title">Company</p>
    <p class="user__text">{{ user.company.name }}</p>
    <p class="user__text user__text_small">{{ user.company.catchPhrase }}</p><br>
    <p class="user__text user__text_small">{{ user.company.bs }}</p>
  </div>
</template>

<script>
export default {
  data: () => ({
    user: {
      address: {
        city: "",
        street: "",
        suite: "",
        zipcode: "",
        geo: {
          lat: "",
          lng: "",
        },
      },
      company: {
        bs: "",
        catchPhrase: "",
        name: "",
      },
      email: "Shanna@melissa.tv",
      id: 0,
      name: "",
      phone: "",
      username: "",
      website: "",
    },
  }),
  mounted() {
    if (localStorage.user) {
      this.user = JSON.parse(localStorage.getItem("user"));
    }
  },
  computed: {
    webLink() {
      return "https://www." + this.user.website;
    },
  },
};
</script>

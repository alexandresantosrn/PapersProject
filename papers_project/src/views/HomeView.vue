<template>
  <div class="main-container">
    <h1>Bem-vindo</h1>
    <Banner v-on:list_users="showUsers"/>
    <div v-show="show_users">
      <UsersList />
    </div>
  </div>
</template>

<script>
import UsersList from '@/components/UsersList.vue';
import Banner from '@/components/Banner.vue';

export default {
  name: 'Homeview',
  data() {
    return {
      show_users: false,
      show_add_user: false,
      show_add_paper: false
    }
  },
  components: {
    UsersList,
    Banner
  },
  methods: {
    showUsers(value) {
      this.show_add_user = false;
      this.show_add_paper = false;
      
      this.show_users = value;
    }
  }

}
</script>


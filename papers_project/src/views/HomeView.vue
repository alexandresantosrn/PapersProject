<template>
  <div class="main-container">
    <h1>Bem-vindo</h1>
    <Banner v-on:list_users="showUsers" v-on:create_users="showCreateUser" v-on:create_papers="showCreatePapers"/>
    
    <div v-show="show_users">
      <UsersList />
    </div>
     
    <div v-show="show_add_user">
      <User />
    </div>

    <div v-show="show_add_paper">
      <Paper />
    </div>

  </div>
</template>

<script>
import Banner from '@/components/Banner.vue';
import UsersList from '@/components/UsersList.vue';
import User from '@/components/User.vue';
import Paper  from '@/components/Paper.vue';

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
    Banner,
    UsersList,
    User,
    Paper
  },
  methods: {
    showUsers(value) {
      this.show_add_user = false;
      this.show_add_paper = false;

      this.show_users = value;
    },
    showCreateUser(value) {
      this.show_users = false;
      this.show_add_paper = false;
      
      this.show_add_user = value;      
    },
    showCreatePapers(valor) {
      this.show_users = false;
      this.show_add_user = false;
      
      this.show_add_paper = true;
    }
  }

}
</script>


<template>
  <div class="main-container">
    <h1>Bem-vindo</h1>
    <Banner />
    <UsersList />
  </div>
</template>

<script>
import UsersList from '@/components/UsersList.vue';
import Banner from '@/components/Banner.vue';

export default {
  name: 'Homeview',
  components: {
    UsersList,
    Banner
  }

}
</script>


<template>
  <div class="main-container">
    <h1>Bem-vindo</h1>
    <UsersList />
  </div>
</template>

<script>
import UsersList from '@/components/UsersList.vue';

export default {
  name: 'Homeview',
  components: {
    UsersList
  }

}
</script>


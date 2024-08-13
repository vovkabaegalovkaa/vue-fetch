<template>
  <div class="container">
    <h1>Работа с БД</h1>
    <form @submit.prevent="acceptData">
      <div class="formControl">
        <label for="name">Введите имя:</label>
        <input type="text" id="name" placeholder="Ваше имя" v-model.trim="name">
      </div>
      <button class="btn accept" :disabled="name.length === 0">Отправить</button>
    </form>
    <app-users-list :users="users" @loadUsers="onLoadUsers"></app-users-list>
  </div>
</template>

<script>
import AppUsersList from './AppUsersList.vue';
export default {
  data(){
    return {
      name: "",
      users: [],
    }
  }, 
  methods: {
    acceptData(){
    },
    onLoadUsers(){
      let response = fetch("http://localhost:81/gallery/back/getComments.php?photoId=13");
      response.then(response => {
        return response.json();
      })
      .then(data => {
        this.users=data;
      })
    }
  },
  components: {
    'app-users-list': AppUsersList,
  }
}
</script>

<style>

</style>

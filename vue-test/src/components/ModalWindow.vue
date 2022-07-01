<template>
  <form class="form" @submit.prevent="addUser">
    <p class="form__title">Добавление пользователя</p>
    <div class="form__item">
      <label for="user-name">Имя</label>
      <input class="user-name" type="text" name="name" v-model.trim="userName" />
    </div>
    <div class="form__item">
      <label for="user-tell">Телефон</label>
      <input class="user-tell" type="text" name="tell" v-model.trim="userTell" />
    </div>
    <div class="form__item">
      <label for="user-parent">Начальник</label>
      <select class="user-parent" name="user-parent" v-model="userParent">
        <option v-for="user in usersContact" :key="user.id" :value="user.id"
          >{{ user.name }}
        </option>
      </select>
    </div>
    <div class="form__button">
      <button
        class="save-button"
        :disabled="userName === '' || userTell === ''"
      >
        Сохранить
      </button>
    </div>
  </form>
</template>

<script>
export default {
  name: "UserTable",
  data() {
    return {
      userName: "",
      userTell: "",
      userParent: null,
    };
  },
  props: {
    usersContact: Array
  },
  methods: {
    addUser() {
        let newUser = {id: Date.now(), name: this.userName, tell:this.userTell, parent: this.userParent}
        this.$emit('addUser', newUser)
        this.userName = ""
        this.userTell = ""
        this.userParent = null
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form {
  width: 40%;
  border: 1px solid;
  padding: 0px 25px;
  font-size: 17px;
}
.form__item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
  align-items: center;
}
.form__title {
  text-align: left;
  margin-bottom: 30px;
}
.user-name,
.user-tell,
.user-parent {
  font-size: 17px;
}
.user-parent {
  width: 229px;
  height: 26px;
}
.form__button {
  display: flex;
  margin-bottom: 20px;
}
.save-button {
  padding: 6px 23px;
  font-size: 15px;
  border-radius: 12px;
  border: 1px solid black;
  transition: 1s ease background;
}
.save-button:hover {
  background-color: rgb(176, 171, 171);
}
</style>

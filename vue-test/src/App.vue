<template>
  <div id="app">
    <div class="container">
      <SectionButton @openModalWindow="openModalWindow" />
      <div class="users">
        <UserTable :usersContact="usersContact" />
        <ModalWindow
          v-if="activeModal"
          :usersContact="usersContact"
          @addUser="addUser"
        />
      </div>
    </div>
  </div>
</template>

<script>
import SectionButton from "./components/SectionButton"
import UserTable from "./components/UserTable"
import ModalWindow from "./components/ModalWindow"

export default {
  name: "App",
  data() {
    return {
      activeModal: false,
      usersContact: [],
    };
  },
  components: {
    SectionButton,
    UserTable,
    ModalWindow
  },
  methods: {
    openModalWindow() {
      this.activeModal = !this.activeModal
    },
    addUser(newUser) {
      this.usersContact.push(newUser)
      localStorage.setItem("usersContact", JSON.stringify(this.usersContact))
      this.activeModal = false
    },
    removeUser() {}
  },
  mounted() {
    this.usersContact = JSON.parse(localStorage.getItem("usersContact")) || []
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
* {
  box-sizing: border-box;
}
button {
  cursor: pointer;
}
p {
  margin: 0;
}
.container {
  max-width: 1170px;
  margin: auto;
}
.users {
  display: flex;
  justify-content: space-between;
}
</style>

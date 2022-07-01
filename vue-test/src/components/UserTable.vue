<template>
  <div class="table">
    <div class="table__heading">
      <p class="table__heading-name" @click="sortByName">Имя</p>
      <p class="table__heading-tell" @click="sortByTell">Телефон</p>
    </div>
    <RowTable
      v-for="user in sortingUsers.filter(item => item.parent === null)"
      :key="user.id"
      :user="user"
      :usersContact="sortingUsers"
    >
    </RowTable>
    <!-- Отрисовка пользователей, у которых нет начальника -->
  </div>
</template>

<script>
import RowTable from "./RowTable.vue"

export default {
  name: "UserTable",
  data() {
    return {
      sortingByName: false,
      sortingByTell: false,
    }
  },
  props: {
    usersContact: Array
  },
  computed: {
    sortingUsers() {
      // делаю перебор по computed свойству, т.к. props нельзя сортировать
      return this.usersContact
    }
  },
  components: { RowTable },
  methods: {
    sortByName() {
      if (this.sortingByName) {
        this.sortingUsers.sort((a, b) => (a.name > b.name ? 1 : -1))
        this.sortingByName = !this.sortingByName
      }
      else {
        this.sortingUsers.sort((a, b) => (a.name < b.name ? 1 : -1))
        this.sortingByName = !this.sortingByName
      }
    },
    sortByTell() {
      if (this.sortingByTell) {
        this.sortingUsers.sort((a, b) => (a.tell > b.tell ? 1 : -1))
        this.sortingByTell = !this.sortingByTell
      }
      else {
        this.sortingUsers.sort((a, b) => (a.tell < b.tell ? 1 : -1))
        this.sortingByTell = !this.sortingByTell
      }
    }
  },
};
</script>

<style scoped>
.table {
  width: 50%;
  border: 1px solid grey;
  border-collapse: collapse;
  height: max-content;
  border: 0;
}
.table__heading {
  display: flex;
  border: 1px solid;
  justify-content: space-around;
  font-weight: 700;
}
.table__heading-name,
.table__heading-tell {
  width: 50%;
  padding: 10px 0;
  cursor: pointer;
  transition: 1s ease color;
}
.table__heading-name:hover,
.table__heading-tell:hover {
  color: rgb(176, 171, 171);
}
.table__heading-tell {
  border-left: 1px solid;
  min-width: 291.5px;
}
</style>

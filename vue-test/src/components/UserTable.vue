<template>
  <div class="table">
    <div class="table__heading">
      <p class="table__heading-name">Имя</p>
      <p class="table__heading-tell">Телефон</p>
    </div>
    <RowTable
      v-for="user in usersContact.filter(item => item.parent === null)"
      :key="user.id"
      :user="user"
      :usersContact="usersContact"
    >
    </RowTable>
  </div>
</template>

<script>
import RowTable from "./RowTable.vue";

export default {
  name: "UserTable",
  comments: {
    RowTable
  },
  props: {
    usersContact: Array
  },
  components: { RowTable }
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
}
.table__heading-tell {
  border-left: 1px solid;
  min-width: 291.5px;
}
</style>

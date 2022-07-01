<template>
  <div class="table__row">
    <div class="table__row-parent">
      <p class="name">{{ user.name }} {{ user.id }}</p>
      <p class="tell">
        {{ user.tell }}
      </p>
    </div>
    <RowTable
      v-for="child in usersContact.filter(item => item.parent === user.id)"
      :key="child.id"
      :usersContact="usersContact"
      :user="child"
      class="table__row-child"
    ></RowTable>
  </div>
</template>

<script>
export default {
  name: "RowTable",
  props: {
    user: Object,
    usersContact: Array
  }
};
</script>
<style>
.table__row-parent {
  border: 1px solid;
  display: flex;
  justify-content: space-between;
  width: 100%;
  min-height: 40px;
  align-items: center;
}
.table__row {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: end;
}
.table__row-child {
  width: 97%;
}
.tell {
  border-left: 1px solid;
  min-width: 291.5px;
  min-height: 40px;
  vertical-align: c;
  display: flex;
  align-items: center;
  justify-content: center;
}
.name {
  padding-left: 15px;
}
</style>

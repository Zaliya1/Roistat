<template>
  <div class="section-button">
    <button class="add-button" @click='openModalWindow'>
      Добавить
    </button>
  </div>
</template>

<script>
export default {
  name: 'SectionButton',
  methods: {
    openModalWindow() {
      this.$emit('openModalWindow')
    },
  }
};
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style >
.section-button {
  width: 50%;
  display: flex;
  justify-content: right;
  margin-bottom: 20px;
}
.add-button {
  padding: 6px 23px;
  font-size: 15px;
  border-radius: 12px;
  border: 1px solid black;
  transition: 1s ease background;
}
.add-button:hover {
  background-color: rgb(176, 171, 171);
}
</style>

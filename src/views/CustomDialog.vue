<template>
  <dialog ref="dialog" class="dialog">
    <div class="header">
      <div class="title">Save changes?</div>
      <span class="close" @click="$emit('close')">X</span>
    </div>

    <div class="content">
      Your changes will not be saved. Do you want to save changes ?
    </div>

    <div class="actions">
      <button @click="$emit('save-changes')">Save</button>
    </div>
  </dialog>
</template>

<script>
export default {
  props: {
    value: Boolean,
  },

  watch: {
    value(val) {
      if (val) this.$refs.dialog.show();
      else this.$refs.dialog.close();
    },
  },
};
</script>


<style scoped>
.header {
  height: 50px;
  box-shadow: inset 0px 4px 9px 5px #eee;
  display: grid;
  grid-template-columns: auto auto;
  justify-content: space-between;
  padding: 0 10px;
  align-items: center;
}

.header > .close {
  font-weight: bold;
  cursor: pointer;
}

.content {
  padding: 20px;
  display: grid;
  place-items: center;
}

.actions {
  padding: 20px;
  display: grid;
  grid-auto-flow: column;
  justify-content: end;
  gap: 10px;
}

.actions button {
  padding: 10px;
}
</style>
<template>
  <div class="home-page">
    <CustomDialog
      :value="showDialog"
      @close="closeDialog"
      @save-changes="saveChanges"
    />
  </div>
</template>

<script>
import CustomDialog from "./CustomDialog";

export default {
  components: {
    CustomDialog,
  },

  data: () => ({
    to: null,
    showDialog: false,
  }),

  beforeRouteLeave(to, from, next) {
    console.log("hi", to, from);
    if (this.to) {
      next();
    } else {
      this.to = to;
      this.showDialog = true;
    }
  },

  methods: {
    closeDialog() {
      this.showDialog = false;
      this.to = null;
    },

    saveChanges() {
      this.showDialog = false;
      this.$router.push(this.to);
    },
  },
};
</script>
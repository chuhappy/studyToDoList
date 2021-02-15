<template>
    <div>
        <input :placeholder="placeholder" v-model="edit" @keyup.enter="enterEvent"/>
        <button v-on:click="editList2"> V </button>
        <button v-on:click="cancelEdit"> X </button>
    </div>
</template>

<script>
export default {
    props: ['placeholder'],
  data () {
    return {
        edit: '',
    }
  },
  methods: {
      editList2() {
          if(this.edit == '') {
              this.$emit('editError', true);
          }
          else if(this.edit !== this.placeholder) {
            this.$emit('editError', false);
            this.$emit('editEvent', this.edit);
            this.edit = '';
          } 
      },
      cancelEdit() {
          this.edit = '';
          this.$emit('cancelEdit');
      },
      enterEvent() {
          this.editList2();
      },
  },
}
</script>
<style scoped>

</style>

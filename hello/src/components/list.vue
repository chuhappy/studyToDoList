<template>
    <li>
            <button v-on:click="changeStatus">{{doMessage}}</button> 
            할일 : {{listData.toDo}}  
            <button v-on:click="editList"> 수정 </button>
            <button v-show="isDo" v-on:click="deleteList"> X </button>
            <edit-list v-show="doEdit" :placeholder="listData.toDo" @editEvent="editEvent" @editError="editError" @cancelEdit="cancelEdit"/>
    </li>
</template>

<script>
import editList from '@/components/editList.vue';

export default {
    components: {editList},
    props: ['listData'],
  data () {
    return {
        isDo: false,
        doMessage: "덜했당",
        doEdit: false,
    }
  },
  computed: {

  },
  watch: {
      isDo(flag) {
          if(flag) {
              this.doMessage = "다헀당"
          } else {
              this.doMessage = "덜했당"
          }
      }
  },
  methods: {
      changeStatus() {
          this.isDo = !this.isDo;
      },
      deleteList() {
          this.$emit('deleteList', this.listData);
      },
      editList() {
          this.doEdit = true;
      },
      editEvent(list) {
          this.$emit('editEvent', list, this.listData);
          this.doEdit  = false;
      },
      editError(flag) {
          this.$emit('editError', flag);
      },
      cancelEdit() {
          this.doEdit = false;
      },
  },
}
</script>
<style scoped>
li {padding:10px;}
</style>

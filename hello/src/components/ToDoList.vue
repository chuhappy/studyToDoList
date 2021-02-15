<template>
<div>
  <div class="toDoList">
    <h2>투 - 두 리스트</h2>
  </div> 

  <div class="makeList">
    <input type="text" v-model="newList" :placeholder="placeholder" @keyup.enter="enterEvent">
    <button v-on:click="click">★추가하기★</button>
  </div>
  <div v-show="isError">
    <p>입력을 해주셔야져?</p>
  </div>

  <div class="thisIsList">
    <ul>
      <list v-for="data in getList" v-bind:key="data['id']" :listData="data" @deleteList="deleteList" @editEvent="editEvent" @editError="editError"></list>
    </ul>
  </div>
</div>
</template>

<script>
import List from '@/components/list.vue';

export default {
  components: {List},
  data () {
    return {
        isError: false,
        newList: '',
        list: [],
        id: 1,
        placeholder: "입력해주십셔",
    }
  },
  computed: {
    getList() {
      return this.list
    },
  },
  methods: {
    editEvent(list, data) {
      this.list[this.list.indexOf(data)].toDo = list;
    },
    enterEvent() {
      this.click();  
    },
    click() {
      if(this.newList !== '') {
        const param = {
            toDo: this.newList,
            id: this.id++,
            isDo: false,
        };
        this.isError = false;
        this.list.push(param);
        this.newList = '';
      } else {
          this.isError = true;
      }
    },
    deleteList(data) {
      this.list.splice(this.list.indexOf(data), 1);
    },
    editError(flag) {
      this.isError = flag;
    },
  },
}
</script>
<style scoped>
ul {list-style: none; color: #fff; font-style: bold;}
.thisIsList {padding-left:200px; text-align: left;}
</style>

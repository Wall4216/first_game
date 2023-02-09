<template>
  <div class="board-wrapper">
    <div class="board">
      <BoardItem v-for="field in field" :key="'item-' + field.id"></BoardItem>
    </div>

      <p class="difficult">Сложность: <strong>{{difficult}}</strong></p>
      <button class="button">Старт:</button>
  </div>
</template>

<script>

import BoardItem from "@/components/BoardItem.vue";
import {onBeforeMount, ref} from "vue";
export default {
  name: "TheBoard",
  components: {
    BoardItem,
  },
  setup(){
    let difficult = ref(5)
    let fields = ref([]);

    const number = 25;

    const init = () => {
      fields.value = []

      for(let i = 0; i<number; i++)
      {
        fields.value.push({
          id: i,
          clicked: false,
          value: 0,
        });
      }
    }

    onBeforeMount(init);
    return {
      difficult,
      fields,
      init
    }
  }
}
</script>

<style scoped>
.board-wrapper{
  margin-bottom:100px ;
}

.board {
  width: 300px;
  background: #eee;
  margin: 0 auto;
}

.button {
  background: green;
  color: white;
  border: none;
  padding: 10px;
  margin: 10px 0;
  cursor: pointer;
  outline: none;
}

button:hover {
background: greenyellow;
}
</style>
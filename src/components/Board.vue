<template>
  <div class="board-wrapper">
    <div class="board">
      <BoardItem v-for="field in fields" :field="field" :key="'item-' + field.id" />
    </div>

    <p class="difficult">Сложность: <strong>{{ difficult }}</strong></p>

    <button class="button" @click="start">Старт</button>
  </div>
</template>

<script>

import BoardItem from './BoardItem.vue';
import { ref, onBeforeMount } from 'vue';
export default {
  name: 'TheBoard',
  props: {},
  components: {
    BoardItem,
  },
  setup() {
    let difficult = ref(15);
    let fields = ref([]);
    const number = 25;

    const init = () => {
      fields.value = [];

      for (let i = 0; i < number; i++) {
        fields.value.push({
          id: i,
          clicked: false,
          value: 0,
        });
      }
    }

    onBeforeMount(init);

    return {
      number,
      difficult,
      fields,
      init
    }
  },
  methods: {
    start() {
      this.init();
      this.Game();
    },

    Game() {
      for (let i = 0; i < this.difficult; i++) {
        const index = this.rand(0, this.number - 1);

        if (this.fields[index].value !== 1) {
          this.fields[index].value = 1;
        } else {
          i--;
        }
      }
    },

    rand(min, max) {
      return Math.floor(Math.random() * (max - min)) + min;
    },
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
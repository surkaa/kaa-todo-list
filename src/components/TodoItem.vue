<template>
  <div class="todo-item">
    <div class="todo-item-flag">
      <el-checkbox v-model="flag" @change="change"></el-checkbox>
    </div>
    <div class="todo-item-content" :class="{'checked': flag}">
      <div class="todo-item-title">
        <span>{{ todo.title }}</span>
      </div>
      <div class="todo-item-desc">
        <span>{{ todo.description }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import {defineComponent} from "vue";

export default defineComponent({
  props: {
    todo: null
  },
  data() {
    return {
      flag: false
    }
  },
  methods: {
    change() {
      if (this.todo.flag === 1) {
        this.todo.flag = 0
        this.flag = false
      } else {
        this.todo.flag = 1
        this.flag = true
      }
    }
  }
})
</script>

<style scoped>
.todo-item {
  display: flex;
  flex-direction: row;
  padding: 1rem 0;
  margin: 1rem;
  border-radius: 1rem;
  background-color: rgba(238, 238, 238, 0.4);
  align-items: center;
}

.checked {
  opacity: 0.1;
  transition: opacity 0.3s;
}

.checked .todo-item-title {
  text-decoration: line-through;
}

.todo-item-flag {
  margin: 1.5rem;
  width: 3rem;
  height: 3rem;
}

.todo-item-content {
  margin: auto 0;
  padding: 0 2rem;
  font-size: 1.8rem;
  font-weight: bold;
  width: calc(100% - 5rem);
  display: flex;
  flex-direction: column;
}

.todo-item-title {
  text-align: left;
  font-size: 2rem;
  font-weight: 800;
  margin-bottom: 1rem;
}

.todo-item-desc {
  font-size: 1rem;
  text-align: left;
  font-weight: 500;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  margin-left: 14px;
}

.todo-item-title::before {
  content: ' - ';
}

>>> .el-checkbox__inner {
  width: 24px;
  height: 24px;
  background-color: rgba(238, 238, 238, 0.7);
}

>>> .el-checkbox__inner::after {
  height: 10px;
  left: 10px;
  top: 4px;
}
</style>
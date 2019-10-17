<template>
<div class="container">
    <div class="col">
      <div class="list-name">To Do</div>
      <draggable :list="list1" class="column-wrapper list-group" draggable=".item" group="a">
        <div
          class="list-group-item item card tile"
          v-for="item in list1"
          :key="item.id"
        >
          {{ item.name }}
        </div>

        <div
          slot="footer"
          class="btn-group list-group-item"
          role="group"
          aria-label="Basic example"
        >
          <input type="text" class="add" @keyup.enter="add($event.target, list1)" placeholder="Add">
        </div>
      </draggable>
    </div>
    <div class="col">
      <div class="list-name">In Progress</div>
      <draggable :list="list2" class="column-wrapper list-group" draggable=".item" group="a">
        <div
          class="list-group-item item card tile"
          v-for="item in list2"
          :key="item.id"
        >
          {{ item.name }}
        </div>

        <div
          slot="footer"
          class="btn-group list-group-item"
          role="group"
          aria-label="Basic example"
        >
          <input type="text" class="add" @keyup.enter="add($event.target, list2)" placeholder="Add">
        </div>
      </draggable>
    </div>
    <div class="col">
      <div class="list-name"> Done</div>
      <draggable :list="list3" class="column-wrapper list-group" draggable=".item" group="a">
        <div
          class="list-group-item item card tile"
          v-for="item in list3"
          :key="item.id"
        >
          {{ item.name }}
        </div>

        <div
          slot="footer"
          class="btn-group list-group-item"
          role="group"
          aria-label="Basic example"
        >
          <input type="text" class="add" @keyup.enter="add($event.target, list3)" placeholder="Add">
        </div>
      </draggable>
    </div>
  </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'TaskBoard',
  components: {
    draggable
  },
  data() {
    return {
      idCounter: 0,
      list1: [],
      list2: [],
      list3: []
    }
  },
  computed: {
  },
  methods: {
    add (target, list) {
      if (target.value) {
        list.push({name: target.value, id: ++this.idCounter})
        target.value = ''
      }
    }
  }
}
</script>

<style scoped>

input {
  border: none;
  outline: none;
}

.container {
	margin: auto;
	margin-top: 50px;
	min-width: 400px;
	display: flex;
	align-items: flex-start;
}

.col {
	background-color: rgba(202, 206, 213, 0.8);
	float: left;
	margin: 10px;
	border-radius: 5px;
	flex-basis: auto;
	flex-grow: 1;
	flex: 1;
	min-width: 200px;
	transition: all 0.2s ease-in-out;
}

.col:hover {
	background-color: rgba(202, 206, 213, 0.95);
}

.card {
	background-color: #fff;
	border-radius: 4px;
	cursor: pointer;
	margin: 15px;
  padding: 7px;
	transition: all 0.3s ease-in-out;
	line-height: 1.5rem;
	box-shadow: 0 1px #aaa;
}

.card div {
	padding: 15px;
}

.column-wrapper {
	min-height: 40px;
}

.list-name {
	color: #1C2640;
	font-size: 1.2rem;
	font-weight: bold;
	padding: 15px;
}

.add {
	display: block;
  font-size: 1.2rem;
	background: none;
	box-shadow: none;
	color: rgba(51, 51, 51, 0.7);
	padding-bottom: 0;
	padding-left: 0;
	padding-top: 0;
}

.add:hover {
	color: #333;
	box-shadow: none;
}

.add {
	padding: 15px;
}

</style>

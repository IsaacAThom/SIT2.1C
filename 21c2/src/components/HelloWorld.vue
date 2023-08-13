<template>
  <!-- Button toggles dark mode -->
  <button class="dark-mode-toggle" @click="darkMode()" title="Toggle Dark Mode">🌙</button>
  <h1>To-Do List</h1>
  <!-- Text field, enter adds new task to list -->
  <input v-model="newTask" @keyup.enter="addTask" placeholder="Enter a new task">
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <div class="row" :class="{ completed: task.completed, important: task.important }">
        <!-- checkbox marks task as complete -->
        <div class="column left">
          <input type="checkbox" v-model="task.completed">
        </div>
        <!-- To-do text -->
        <div class="column main task">
          {{  task.text }}
        </div>
        <!-- buttons for moving tasks up/down the list, marking them as important, and removing them -->
        <div class="column right">
          <button @click="upTask(index)" title="Move Up">🔺</button>
          <button @click="downTask(index)" title="Move Down">🔻</button>
          <button @click="task.important = !task.important" title="Mark as Important">❗</button>
          <button @click="removeTask(index)" title="Remove Task">❌</button>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  // Create blank array on launch
  data() {
    return {
      newTask: '',
      tasks: []
    };
  },
  methods: {
    // Adds value to array if text field isnt blank
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({
          text: this.newTask,
          completed: false,
          important: false,
        });
        this.newTask = '';
      }
    },
    // Swaps selected task with the one above it, only if it isn't at the top of the list
    upTask(index) {
      if (index > 0) {
        let temp = this.tasks[index];
        this.tasks[index] = this.tasks[index - 1];
        this.tasks[index - 1] = temp;
      }
    },
    // Swaps selected task with the one below it, only if it isn't at the bottom of the list
    downTask(index) {
      let lastElement = this.tasks.length - 1;
      if (index < lastElement) {
        let temp = this.tasks[index];
        this.tasks[index] = this.tasks[index + 1];
        this.tasks[index + 1] = temp;
      }
    },
    // Removes task from array
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
    // Toggles dark mode
    darkMode() {
      if (document.body.classList == 'dark-mode') {
        document.body.classList.remove('dark-mode');
      } else {
        document.body.classList.add('dark-mode');
      }
    }
  }
}
</script>


<style scoped>
ul {
  margin: 0px 100px;
  padding: 0px;
}

li {
  list-style: none;
}

/* Columns */
.row {
  margin: 10px 5px;
  border: 1px solid #000;
  border-radius: 5px;
  background-color: var(--bgColor2);
  box-shadow: var(--boxShadow1);
  display: flex;
  justify-content: center;
  align-items: center;
  transition: background-color 0.5s, text-color 0.5s, box-shadow 0.5s;
}

.row:hover {
  background-color: var(--bgColor2Hover);
  box-shadow: var(--boxShadow2);
}

.column {
  float: left;
}

.left {
  width: 20%;
}
.main {
  width: 60%;
  border-left: 1px solid #000;
  border-right: 1px solid #000;
  padding: 15px;
}

.right {
  width: 20%;
}

.row:after {
  content: "";
  display: table;
  clear: both;
}

/* list items + their different states */
.task {
  background-color: var(--bgColor2);
  transition: background-color 0.5s, text-color 0.5s;
}

.task:hover {
  background-color: var(--bgColor2Hover);
}

.row.important,
.important .task {
  background-color: var(--bgColor3);
  font-weight: bold;
}

.row.important:hover,
.important .task:hover {
  background-color: var(--bgColor3Hover);
}

.row.completed,
.completed .task {
  background-color: var(--bgColor4);
  font-weight: normal;
  text-decoration: line-through;
}

.row.completed:hover,
.completed .task:hover {
  background-color: var(--bgColor4Hover);
}
/* Header */
h1 {
  border-bottom: 1px solid var(--textPrimary);
}
/* Buttons */
button {
  margin: 0px 2px;
  box-shadow: var(--boxShadow1);
}

button:hover {
  box-shadow: var(--boxShadow2);
}

@media screen and (max-width: 800px) {
  .row {
    display: block;
  }
  .left, .main, .right {
    width: 100%;
    padding: 5px 0px;
  }
  .main {
    border-top: 1px solid #000;
    border-bottom: 1px solid #000;
    border-left: none;
    border-right: none;
  }
}
</style>

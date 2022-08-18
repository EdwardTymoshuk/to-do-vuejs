<template>
<div>
          <div class="addTask container">
          <div class="addTask-container">
            <b-form-input id="input-large" type="text" @keyup.enter="addTask" v-model="currentTask" placeholder="Enter a new task..."></b-form-input>
            <b-button type="button" class="btn btn-dark" @click="addTask" >Add new task!</b-button>
          </div>
        </div>
        <div class="tasksList">
          <b-list-group :key="tasks[task]" v-for="task in tasks">
            <b-list-group-item class="d-flex justify-content-between align-items-center">
              <div class="taskList-changeTask" v-if="task.isEditing === true">
                <b-form-input id="input-large" v-model="editValue" @keyup.enter="changeTask(task.text)"></b-form-input>
                <b-button variant="success" type="button" @click="changeTask(task.text)"><b-icon icon="check"></b-icon></b-button>
              </div>
              <span v-else :class="{'strike': task.isComplited}">{{task.text}}</span>
              <div>
                <b-button-group>
                    <b-button variant="success" type="button" title="Complete task" v-if="task.isComplited === false" @click="setComplitedTask(task)"><b-icon icon="check-all"> </b-icon></b-button>
                    <b-button variant="warning" type="button" title="Uncomplete task"  v-else @click="setComplitedTask(task)"><b-icon icon="reply-fill"></b-icon></b-button>
                    <b-button variant="info" type="button" title="Edit task"  @click="changeEditing(task.text)"><b-icon icon="pencil"> </b-icon></b-button>
                    <b-button variant="danger" type="button" title="Delete task"  @click="removeTask(task.text)"><b-icon icon="x"> </b-icon></b-button>
                </b-button-group>
              </div>
            </b-list-group-item>
          </b-list-group>
        </div>
        </div>
</template>

<script>
export default {
    data() {
    return {
        tasks: [
      {
        text: 'Learn Vue.js',
        isComplited: false,
        isEditing: false
      },
      {
        text: 'Learn React.js',
        isComplited: true,
        isEditing: false
      },
      {
        text: 'Learn Angular.js',
        isComplited: false,
        isEditing: false
      }
    ],
    currentTask: '',
    editValue: ''
    }
  }, 
  methods: {
    addTask() {
      this.currentTask
      &&
      this.tasks.push({
        text: this.currentTask,
        isComplited: false
      })
      this.currentTask = ''
    },
    setComplitedTask(task) {
      task.isComplited = !task.isComplited
    },
    removeTask(taskText) {
      this.tasks = this.tasks.filter(task => task.text !== taskText)
    },
    changeEditing(taskText) {
      this.editValue = taskText;
      this.tasks = this.tasks.map(task => {
        if (task.text === taskText) {
          task.isEditing = !task.isEditing
        }
        return task
      })

    },
    changeTask(taskText) {
      this.tasks = this.tasks.map(task => {
        if (task.text === taskText) {
          task.isEditing = !task.isEditing
          task.text = this.editValue
        }
        return task
      })

    }
  },
  computed: {
    
  }
}
</script>

<style scoped>
  .addTask {
    display: grid;
    align-self: center;
    width: 100vw;
    margin: 50px 0;
}
.addTask-container {
    display: grid;
    width: 50%;
    justify-self: center;
}
.addTask input {
    margin-bottom: 10px;
}
.addTask button {
    cursor: pointer;
    inline-size: fit-content;
    justify-self: center;
}
.tasksList {
    color: #50514F;
    font-size: 1.5em;
}
.taskList-changeTask {
  display: flex;
}
.taskList-changeTask button{
  margin-left: 10px
}
</style>
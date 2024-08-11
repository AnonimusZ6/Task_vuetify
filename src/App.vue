<template>
  <v-container>
    <v-row>
      <v-col>
        <v-banner-text style="font-size: 35px">Список дел</v-banner-text>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-text-field
          v-model="newTask"
          label="Добавить новую задачу"
          @keyup.enter="addTask"
        ></v-text-field>
        <v-btn @click="addTask">Добавить</v-btn>
      </v-col>
    </v-row>

    <v-list>
      <v-list-item-group>
        <v-list-item
          v-for="(task, index) in tasks"
          :key="index"
          :class="{ completed: task.completed }">
          <v-list-item-content>
            <v-list-item-title>{{ task.text }}</v-list-item-title>
            <v-list-item-action>
              <v-btn icon @click="removeTask(index)">
                <v-icon>mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ title: this.titleTask, text: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style scoped>
</style>
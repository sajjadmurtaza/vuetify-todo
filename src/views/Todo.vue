<template>
  <div class="todo pa-6">
    <h1>Todo Page</h1>
    <v-list
      class="pt-0"
      flat
    >
      <div
        v-for="task in tasks"
        :key=task.id
      >

        <v-list-item
          @click="doneTask(task.id)"
          :class="{ 'blue lighten-4' : task.done }"
        >

          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content
              :class="{ 'text-decoration-line-through' : task.done }"
            >
              <v-list-item-title>
                {{task.title}}
              </v-list-item-title>

              <v-list-item-subtitle>
                {{task.time}}
              </v-list-item-subtitle>
            </v-list-item-content>

          </template>
        </v-list-item>

        <v-divider></v-divider>
      </div>

    </v-list>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  // add data method that return an object
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: 'Wake up',
          time: 'at 8:00',
          done: false
        },
        {
          id: 2,
          title: 'Gym',
          time: 'at 18:00',
          done: true
        },
        {
          id: 3,
          title: 'Weekly plus',
          time: 'at 19:00',
          done: false
        }
      ]
    }
  },
  methods: {
    doneTask(id) {
      console.log(id)

      // filter method will itrate each of task in array
      // filter will return array of object: not single object
      // that's why we need to get first element with [0]
      let task = this.tasks.filter(task => task.id === id)[0]

      task.done = !task.done
    }
  }
}
</script>

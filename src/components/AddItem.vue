<template>
  <div>
    <form @submit="add">
      <input type="text" v-model="title" name="title" placeholder="Add Todo" />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
// import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'AddItem',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    add(event) {
      event.preventDefault();

      const newItem = {
        // id:uuidv4(),
        title: this.title,
        completed: false,
      };

      // send up to parent

      this.$emit('add-todo', newItem);

      this.title = '';
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type='text'] {
  flex: 10;
  padding: 5px;
}

input[type='submit'] {
  flex: 2;
}
</style>

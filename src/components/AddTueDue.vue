<template>
  <form @submit="onSubmit" class="addForm">
    <div class="addForm__group">
      <label for="text">Tue Due</label>
      <input type="text" v-model="text" name="text" placeholder="Buy apples" />
    </div>
    <div class="addForm__group">
      <label for="day">Day & Time</label>
      <input type="text" v-model="day" name="day" placeholder="May 2 at 2:30pm" />
    </div>
    <div class="addForm__group">
      <label for="reminder">Day & Time</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>
    <input type="submit" value="Save Tue-Due" class="btn" />
  </form>
</template>

<script>
export default {
  name: 'AddTueDue',
  emits: ['addTueDue'],
  data() {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if(!this.text) {
        alert('Please add a Tue-Due')
        return;
      }
      
      const newTueDue = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }

      this.$emit('addTueDue', newTueDue);

      this.text = '',
      this.day = '',
      this.reminder = false
    }
  }
}
</script>

<style scoped>
.addForm {
  margin: 1rem;
  padding: 1rem;
  border: 1px solid grey;
  border-radius: .25rem;
}
</style>

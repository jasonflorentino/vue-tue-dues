<template>
  <div class="container">
    <Header title='Vue Tue-Due App' />
    <AddTueDue @addTueDue="addTueDue" />
    <TueDues 
      @toggle-reminder="toggleReminder"
      @delete-tueDue="deleteTueDue" 
      :tueDues="tueDues" 
    />
  </div>
</template>

<script>
import Header from './components/Header';
import TueDues from './components/TueDues';
import AddTueDue from './components/AddTueDue';

export default {
  name: 'App',
  components: {
    Header,
    TueDues,
    AddTueDue
  },
  data() {
    return {
      tueDues: []
    }
  },
  methods: {
    addTueDue(tueDue) {
      this.tueDues = [...this.tueDues, tueDue]
    },
    deleteTueDue(id) {
      if (confirm('Are you sure?')) {
        this.tueDues = this.tueDues.filter(tueDue => tueDue.id !== id);
      }
    },
    toggleReminder(id) {
      this.tueDues = this.tueDues.map(
        tueDue => tueDue.id === id 
          ? {...tueDue, reminder: !tueDue.reminder} 
          : tueDue
      )
    }
  },
  created() {
    this.tueDues = [
      {
        id: 1,
        text: 'Learn some Vue',
        day: 'May 1st at 2:30pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Finish this App',
        day: 'May 2nd at 11:30am',
        reminder: true
      },
      {
        id: 3,
        text: 'Have a cuppa tea',
        day: 'May 2nd at 12:00pm',
        reminder: false
      },
    ]
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 2rem;
  background-color: #fafafa;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.container {
  padding: 1rem;
  border: 1px solid #cccccc;
  border-radius: .25rem;
  background-color: white;
}

</style>

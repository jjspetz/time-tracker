<template>
  <div class="form-horizontal">
    <div class="form-group">
      <div class="col-sm-6">
        <label>Date</label>
        <input
          type="date"
          class="form-control"
          v-model="timeEntry.date"
          placeholder="Date"
        />
      </div>
      <div class="col-sm-6">
        <label>Hours</label>
        <input
          type="number"
          class="form-control"
          v-model="timeEntry.totalTime"
          placeholder="Hours"
        />
      </div>
    </div>
    <div class="form-group">
      <div class="col-sm-12">
        <label>Comment</label>
        <input
          type="text"
          class="form-control"
          v-model="timeEntry.comment"
          placeholder="Comment"
        />
      </div>
    </div>
    <button class="btn btn-primary" @click="save()">Save</button>
    <router-link
        v-bind:to="'/time-entries/'">
          <a class="btn btn-primary">Cancel</a>
      </router-link>
    <hr>
  </div>

</template>

<script>
  import eventHub from '../EventHub'

  export default {
    data () {
      return {
        // We default the user object on
        // the timeEntry to have some user details
        timeEntry: {
          user: {
            firstName: 'JJ',
            lastName: 'Spetseris',
            email: 'jj.spetseris@yahoo.com',
            image: '/docs/static/portrait.png'
          }
        }
      }
    },
    methods: {
      save() {
        if (this.timeEntry.totalTime) {
          let timeEntry = this.timeEntry
          eventHub.$emit('save', timeEntry)
          this.timeEntry = {
            user: {
              firstName: 'JJ',
              lastName: 'Spetseris',
              email: 'jj.spetseris@yahoo.com',
              image: '/docs/static/portrait.png'
            }
          }
        }
      }
    }
  }
</script>

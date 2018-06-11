<template>
  <div id="app" class="container">
    <div class="page-header">
      <h1>Work Tracker</h1>
    </div>
    <div class="panel panel-default">
      <div class="panel-heading">
        <h1>Add Time</h1>
      </div> 
      <div class="panel-body">
        <input type="button" class="btn btn-primary" value="Add Time" v-on:click.prevent="addTime">
      </div> 
    </div>
    <div class="panel panel-default">
      <div class="panel-heading">
        <h3>Times list</h3>
      </div>
    <div class="panel-body">
      <table class="table table-striped">
        <thead>
            <tr>
                <th>
                  Time
                </th>
              </tr>
        </thead>
        <tbody>
          <tr v-for="vrijeme in times">
            <td>
              {{vrijeme.exctime}}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    </div>

  </div>
  
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Firebase from 'firebase'

let config = {
  apiKey: "AIzaSyCgPcM6HtmIa-lfYCp72Z0lL7VlvJ-0q7I",
  authDomain: "vue-time-tracker-c61d6.firebaseapp.com",
  databaseURL: "https://vue-time-tracker-c61d6.firebaseio.com",
  projectId: "vue-time-tracker-c61d6",
  storageBucket: "vue-time-tracker-c61d6.appspot.com",
  messagingSenderId: "988137714713"
}

let app = Firebase.initializeApp(config);
let db = app.database();
let timesRef = db.ref('times');

export default {
  name: 'app',
  firebase: {
    times: timesRef
    
  },
  data () {
    return {
      newTime: {
        exctime: '',
      }
    }
  },
  methods: {
    addTime: function(){
      timesRef.push({
        time: $scope.createdDate = firebase.database.ServerValue.TIMESTAMP;
      });
      this.newTime.exctime = '';
    }
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

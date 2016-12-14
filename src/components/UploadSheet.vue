<template>
<div class="bgcolor">
  <ul>
    <li><a class="active" @click="ChangePage(1)">Home</a></li>
    <li><input type="search" class="search"></li>
    <li><a @click="ChangePage(1)">Read</a></li>
    <li><a href="#about">About</a></li>
  </ul>
  <div class="form-style-6">
    <h1>Upload File</h1>
    <form>
      <input type="text" name="subject" placeholder="Subject" class="subject" v-model="newSubject"/>
      <input type="text" name="title" placeholder="Title" class="subject"/>
      <input type="file" name="choosfile" placeholder="Choose File" class="choose" value="Choose File" accept="application/pdf"/>
      <!--<input type="submit" value="Choose File" class="choosefile"/>-->
      <input type="submit" value="Upload" class="canup"/><input type="submit" value="Cancle" class="canup"/>
    </form>
  </div>
</div>
</template>

<script>
var emailRE = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
var firebase = require('firebase/app')
require('firebase/auth')
require('firebase/database')

// Initialize Firebase
var config = {
  apiKey: 'AIzaSyCq9l98zJYY7iDJG0dWphAOULQEf39lmwM',
  authDomain: 'sheetato.firebaseapp.com',
  databaseURL: 'https://sheetato.firebaseio.com',
  storageBucket: 'sheetato.appspot.com',
  messagingSenderId: '196311840371'
}
firebase.initializeApp(config)
export default {
  props: ['ChangePage'],
  name: 'upload',
  data () {
    return {
      subject: [],
      newSubject: ''
    }
  },
  computed: {
    validation () {
      return {
        newSubject: !!this.newSubject.trim()
      }
    },
    isValid () {
      var validation = this.validation
      return Object.keys(validation).every(function (key) {
        return validation[key]
      })
    }
  },
  methods: {
    addSubject: function () {
      if (this.isValid) {
        newSubject.push(this.newSubject)
        this.newSubject = ''
      }
    }
  },
  mounted () {
    let vm = this
    Subject.on('child_added', function (snapshot) {
      var item = snapshot.val()
      item.id = snapshot.key
      vm.newSubject.push(item)
    })
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Raleway');

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
}

li {
  float: left;
}

li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover {
  background-color: #F8F8FF;
  color: #000000;
}

.active {
  background-color: #333;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.search {
  border-radius: 8px;
  width: 230px;
  height: 30px;
  margin-top: 8px;
  margin-left: 790px;
}

.form-style-6{
    font-family: 'Raleway', sans-serif;
    max-width: 500px;
    height: 320px;
    margin: 10px auto;
    margin-top: 100px;
    padding: 20px;
    background: #F7F7F7;
}
.form-style-6 h1{
    background: #000000;
    padding: 20px 0;
    font-size: 140%;
    font-weight: 300;
    text-align: center;
    color: #fff;
    margin: -16px -16px 16px -16px;
}

.subject
{
    -webkit-transition: all 0.30s ease-in-out;
    -moz-transition: all 0.30s ease-in-out;
    -ms-transition: all 0.30s ease-in-out;
    -o-transition: all 0.30s ease-in-out;
    outline: none;
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    width: 100%;
    background: #fff;
    margin-bottom: 4%;
    border: 1px solid #ccc;
    padding: 3%;
    color: #555;
    font: 95% 'Raleway', Helvetica, sans-serif;
}
.subject input[type="text"]:focus,
.subject select:focus
{
    padding: 3%;
    border: 1px solid #000000;
}

.choose
{
    -webkit-transition: all 0.30s ease-in-out;
    -moz-transition: all 0.30s ease-in-out;
    -ms-transition: all 0.30s ease-in-out;
    -o-transition: all 0.30s ease-in-out;
    outline: none;
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    width: 100%;
    background: #fff;
    margin-bottom: 4%;
    border: 1px solid #ccc;
    padding: 3%;
    color: #555;
    font: 95% 'Raleway', Helvetica, sans-serif;
}
.choose input[type="text"]:focus,
.choose select:focus
{
    padding: 3%;
    border: 1px solid #000000;
}
.choosefile{
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    width: 30%;
    padding: 3%;
    background: #000000;
    margin-bottom: 5px;
    color: #ffffff;
    font-family: 'Raleway', sans-serif;
    display: inline-block;
}
.choosefile:hover,
.choosefile:hover{
    background: #ffffff;
    color: #000000;
}

.canup{
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    width: 50%;
    padding: 3%;
    background: #000000;
    margin-bottom: 5px;
    color: #ffffff;
    font-family: 'Raleway', sans-serif;
    display: inline-block;
}
.canup:hover,
.canup:hover{
    background: #ffffff;
    color: #000000;
}

.bgcolor {
  background-color: #F5F5F5;
  width: 100vu;
  height: 100vh;
}

</style>

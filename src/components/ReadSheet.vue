<template>
  <div class="bgcolor">
  <ul>
    <li><a class="active" @click="ChangePage(1)">Home</a></li>
    <li><input type="search" class="search"></li>
    <li><a @click="ChangePage(2)">Upload</a></li>
    <li><a href="#about">About</a></li>
  </ul>
  <div class="form-style-6" v-for="name in subject">
    <h1>{{name}}</h1>
    <form>
      <input type="submit" value="Read More >" class="canup"/>
    </form>
  </div>
</div>
</template>

<script>
export default {
  props: ['ChangePage'],
  data () {
    return {
      subject: ['Network Programming', 'App Mobile', 'Net Design', 'Net Lab II', 'Com Pro', 'Database', 'Net Lab II', 'Com Pro', 'Database'],
      gotoupload: false
    }
  },
  methods: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

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
  margin-left: 770px;
}

.form-style-6{
    font-family: 'Raleway', sans-serif;
    max-width: 400px;
    height: 120px;
    margin-top: 20px;
    margin-left: 30px;
    margin-right: 20px;
    margin-right: 20px;
    padding: 20px;
    background: #F8F8FF;
    box-shadow: 1px 1px 1px 0.5px #DCDCDC;
    display: inline-block;
    width: 350px;
}
.form-style-6 h1{
    background: #000000;
    padding: 20px 0;
    font-size: 200%;
    font-weight: 300;
    text-align: center;
    color: #fff;
    margin: -16px -16px 16px -16px;
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

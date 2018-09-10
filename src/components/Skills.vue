<template>
  <div class="hello">
    <div class="holder">
      <ul>
        <li v-for="(data,index) in skills" :key = 'index'>{{ data.skill }}</li>


      </ul>

      <!-- <div v-bind:class="{alert: showAlert, ' another-class': showClass}">
      </div> -->
      <div v-bind:class="alertObject"></div>

      <p v-if="skills.length >= 1">You have more than 1 skills</p>
      <p v-else>You have less or 1 skill</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data(){
    return {
      skills : [
        { "skill" : "vue.js"},
        { "skill" : "Front End Developer"}
      ],
      // showAlert: true,
      // showClass: true
      alertObject:{
        alert:false
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .alert {
    background-color: #eeeeee;
    width: 100%;
    height: 35px;
  }
  .another-class {
    border: 2px solid blue;
  }
  .holder {
    background: #fff;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }
</style>

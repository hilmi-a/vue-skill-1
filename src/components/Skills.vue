<template>
  <div class="hello">
    <div class="holder">
      <ul>
        <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter the Skill you have..." v-model="skill" v-validate="'min:5'" name="skill">
        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
        <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill')}}</p>
        </transition>
        <!-- {{ skill }} -->
       <!--  <input type="checkbox" id="checkbox" v-model="checked"> -->
        </form>
          <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
            <li v-for="(data,index) in skills" :key = 'index'>{{ data.skill }}
              <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
            </li>
          </transition-group>

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
      // checked: false,
      skill: '',
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
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          this.skills.push({skill: this.skill});
      this.skill= '';
      // console.log('this checkbox value is : '+this.checked);
        }else {
          console.log('Not valid');
        }
      })
    },
    remove(id) {
      this.skills.splice(id,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.2";
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css";
  .alert {
    background-color: #eeeeee;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
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

  input {
    width: calc(100% - 40px);
    border:0;
    padding: 20px;
    font-size: 1.3em;
    background: #323333;
    color: #687f7f;
  }

  .alert-in-enter-active {
    animation: bounce-in .5s;
  }

  .alert-in-leave-active {
    animation: bounce-in .5s reverse;
  }

  @keyframes bounce-in {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.5);
    }
    100% {
      transform: scale(1);
    }
  }

  i {
    float: right;
    cursor: pointer;
  }
</style>

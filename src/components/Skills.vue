<template>
  <div class="hello">
    <div class="holder">

      <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill">

        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
          <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>
      </form>

      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in skills" :key='index'>
            {{ data.skill }}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
      </ul>

      <p>These are the skills that you possess.</p>
    </div>
</div>
</template>

<script>
export default {
    name:'Skills',
    data() {
        return{
            // name: 'Dax',
            // btnState:true,
            // checked:false,
            skill: '',
            skills : [
                {"skill":"vue.js"},
                {"skill":"PHP"},
                {"skill":"Laravel"},
                {"skill":"Angular"}
            ]
            // showAlert: true,
            // showClass : true
        }
    },
    methods:{
        addSkill(){
            this.$validator.validateAll().then((result)=>{
                if(result){
                this.skills.push({skill:this.skill})
                this.skill="";
                }else{
                    console.log('Not Valid');
                }
            })
            
                // console.log('this checkbox value is : '+ this.checked)
        }
    }
   
}
</script>
<style scoped>
/* .alert{
    background-color: red;
    width: 100%;
    height: 20%;
    
}
.another-class{
    border:5px solid green;
} */
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"; 
.holder{
    background: #ffff;

}
i {
  float:right;
  cursor:pointer;
}
ul{
    margin:0%;
    padding: 0%;
    list-style-type: none;
}
ul li {
    padding: 20px;
    font-size: 1.3em;
    background: #E0EDF4;
    border-left: 5px solid #3ed3f6;
    margin-bottom: 2px;
    color: #3e5252;
}
p{
    text-align: center;
    padding: 30px 0;
    color: grey;
}
.container{
    box-shadow: 0px 0px 40px lightgray;
}
input{
    width: calc(100%-40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687f7f;
}
.alert{
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
    
    }

    .alert-in-enter-active{
        animation:bounce-in .5s;
    }
      .alert-in-leave-active{
        animation:bounce-in .5s reverse;
    }

    @keyframes bounce-in {
        0%{
            transform: scale(0);
        }
        50% {
            transform: scale(1.5);
        }
        100% {
            transform: scale(1);
        }
        
    }
</style>

/*
    Requirements: font-awesome, bootstrap
    How to instantiate this component: 
    input-password v-model="form.myPassword" :pid="'myPassword'" v-on:input-event="InputPassword"/>

    declare in method:
    InputPassword: function(param){
      this.form.myPassword = param;
    }    

*/
<template>
  <div class="input-group">
    <input class="form-control" :id="pid"  type="password" v-model="value" required v-on:input="InputEvent"/>
    <div class="input-group-append">
      <span class="input-group-text" @click="passwordShowHide()">
        <i class="fas fa-eye d-none p-hand" :id="'showEye' + pid"></i>
        <i class="fas fa-eye-slash p-hand" :id="'hideEye' + pid"></i>
      </span>
    </div>
  </div>
</template>

<script>
export default {
data(){
    return{
        value: "",
    }
},
  props: ["pid"],

  methods: {
    passwordShowHide() {
      let showEye = document.getElementById("showEye" + this.$props.pid);
      let hideEye = document.getElementById("hideEye" + this.$props.pid);

      if (showEye.classList.contains("d-none")) {
        document.getElementById(this.$props.pid).type = "text";
        showEye.classList.remove("d-none");
        hideEye.style.display = "none";
      } else {
        document.getElementById(this.$props.pid).type = "password";
        showEye.classList.add("d-none");
        hideEye.style.display = "inline-block";
      }
    },
    InputEvent: function(){
        this.$emit('input-event',  this.value);
    }
  },
};
</script>


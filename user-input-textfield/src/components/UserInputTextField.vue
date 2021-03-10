<template>
  <div id="user-text-field">
    <input id="input-id" :type="checkedType" :required="required ? true : false" @input="handleInput" />
    <label id="label-id" for="user-text-field">{{ name }}</label>
    <i id="icon-id" :class="`bi-${icon}`"></i>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: "",
    };
  },
  props: {
    height: String,
    width: String,
    name: String,
    type: String,
    icon: String,
    required: Boolean,
    error: Boolean,
    errCallback: Function,
  },
  computed: {
    checkedType() {
      if (this.type != "") {
        if (!this.validType(this.type)) {
          if(this.errCallback){
            this.errCallback("invalid type, defaulting to text type");
          }    
          return "text";
        }
        return this.type;
      } else {
        return "text";
      }
    },
  },
  methods: {
    validateSize(size) {
      return /\s*(\d+)px|\s*(\d+)rem|\s*(\d+)em/.test(size);
    },
    handleInput(e) {
      this.input = e.target.value;
      this.$emit("input", e.target.value);
    },
    validType(type) {
      return ["text", "email", "password"].includes(type);
    },
  },
  mounted(){
    document.getElementById('user-text-field').addEventListener('mouseover', ()=>{
      document.getElementById('user-text-field').classList.add('mouseOver')
    });
    document.getElementById('user-text-field').addEventListener('mouseout', ()=>{
      let activeElem = document.getElementById('input-id')
      // check if input is not focus and there is an input value
      if(activeElem !== document.activeElement && document.getElementById('input-id').value === ""){
        document.getElementById('user-text-field').classList.remove('mouseOver')
      }
      
    })
    document.getElementById('input-id').addEventListener('focusin', ()=>{
      document.getElementById('label-id').classList.add('focusIn')
      document.getElementById('user-text-field').classList.add('mouseOver')
    })
    document.getElementById('input-id').addEventListener('focusout', ()=>{
      // check if there is an input value
      if(document.getElementById('input-id').value === ""){
        document.getElementById('label-id').classList.remove('focusIn')
        document.getElementById('user-text-field').classList.remove('mouseOver')
      }     
    })

    // spacing adjustments
    if(!this.icon){
      document.getElementById('input-id').style.left = '10px'
      document.getElementById('label-id').style.left = '10px'
    }
  },
  watch: {
    height: function (newVal, oldVal) {
      if (newVal !== oldVal) {
        if (this.validateSize(newVal)) {
          document.getElementById("user-text-field").style.height = newVal;
        } else {
          // revert to default
          document.getElementById("user-text-field").style.height = "40px";
          throw Error("only accepts rem, em, px");
        }
      }
    },
    width: function (newVal, oldVal) {
      if (newVal !== oldVal) {
        if (this.validateSize(newVal)) {
          document.getElementById("user-text-field").style.width = newVal;
        } else {
          // revert to default
          document.getElementById("user-text-field").style.width = "100%";
          throw Error("only accepts rem, em, px");
        }
      }
    },
    error: function(newVal){
      if(newVal === true){
        document.getElementById('label-id').classList.add('error')
        document.getElementById('user-text-field').classList.add('error')
      }
      else{
        document.getElementById('label-id').classList.remove('error')
        document.getElementById('user-text-field').classList.remove('error')
      }
    }
  },
};
</script>

<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.4.0/font/bootstrap-icons.css");

i {
  position: absolute;
  top: calc(50% - 14px);
  left: 10px;
  font-size: 1.5rem; 
  color: grey
}

.bi::before {
  content: "";
  vertical-align: -0.125em;
  background-image: url("data:image/svg+xml,<svg viewBox='0 0 16 16' fill='%23333' xmlns='http://www.w3.org/2000/svg'><path fill-rule='evenodd' d='M8 9.5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3z' clip-rule='evenodd'/></svg>");
  background-repeat: no-repeat;
  background-size: 1rem 1rem;
}

#user-text-field {
  position: relative;
  height: 40px;
  width: 200px;
  border: 2px solid #9c9a9ace;
  border-radius: 5px;
}

input {
  position: absolute;
  left: 40px;
  height: 100%;
  width: calc(100% - 45px);
  padding: 0;
  border: 0;
  outline: 0;
  background-color: transparent;
}

label {
  position: absolute;
  top: calc(50% - 10px);
  left: 40px;
  transition: 0.2s all;
  text-align: left;
  cursor: text;
  color: grey;
}

/* Error Animations and Colors */
.error{
  animation: shake 0.4s forwards ease-out;
}

.error.focusIn{
  color:#9b392c;
}

#user-text-field.error.mouseOver{
  border-color: #9b392c;
}

#user-text-field.error.mouseOver > i{
  color: #9b392c;
}

/* Default Colors */
#user-text-field.mouseOver{
  border-color: #549b2c;
}

#user-text-field.mouseOver > i{
  color: #549b2c;
}

label.focusIn{
  font-size: 14px;
  top: -10px;
  background: white;
  z-index: 100;
  color: #549b2c;
  padding: 0 5px;
}

@keyframes shake{
  0%, 100%{
    transform: translate(0px,0px);
  }
  14%{
    transform: translate(-10px,0px);
  }
  28%{
    transform: translate(10px,0px);
  }
  42%{
    transform: translate(-10px,0px);
  }
  56%{
    transform: translate(10px,0px);
  }
  70%{
    transform: translate(-10px,0px);
  }
  84%{
    transform: translate(10px,0px);
  }
}

</style>
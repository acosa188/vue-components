<template>
  <div id="user-text-field">
    <input type="text" required @input="handleInput" />
    <label for="user-text-field">{{ name }}</label>
    <i class="bi-person-fill" style="font-size: 1.5rem; color: grey"></i>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: "",
    };
  },
  props: ["height", "width", "name"],
  methods: {
    validateSize(size) {
      return /\s*(\d+)px|\s*(\d+)rem|\s*(\d+)em/.test(size);
    },
    handleInput(e) {
      this.input = e.target.value;
      this.$emit("input", e.target.value);
    },
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
    input: function(newVal){
        console.log("got here")
        if(newVal !== ""){
            document.getElementById("user-text-field").style.borderColor = '#549b2c';
        }else{
            document.getElementById("user-text-field").style.borderColor = '#9c9a9ace';
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

#user-text-field:hover,
#user-text-field:focus-within {
  border-color: #549b2c!important;
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
  z-index: -100;
  color: grey;
}
input:focus ~ label,
input:valid ~ label {
  font-size: 14px;
  top: -10px;
  background: white;
  z-index: 100;
  color: #549b2c;
  padding: 0 5px;
}

#user-text-field:hover > i,
input:valid ~ i,
input:focus ~ i {
  color: #549b2c !important;
}
</style>
<template>
  <div>
    <button class="btn">
      <span> LOGIN </span>
      <div class="icon">
        <i class="fa fa-remove"></i>
        <i class="fa fa-check"></i>
      </div>
    </button>
  </div>
</template>

<script>
export default {
  name: "UserButton",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn {
  display: block;
  position: relative;
  background-color: #549b2c;
  color: #fff;
  border: none;
  border-radius: 5px;
  outline: none;
  height: 100px;
  width: 300px;
  cursor: pointer;
  margin: auto;
  box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.3);
  transition: all 0.2s cubic-bezier(0.31, -0.105, 0.43, 1.4);
}

.btn > span,
.btn > .icon {
  height: 100%;
  text-align: center;
  position: absolute;
  top: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.btn > span {
  width: 72%;
  line-height: inherit;
  font-size: 22px;
  text-transform: uppercase;
  left: 0;
  transition: all 0.2s cubic-bezier(0.31, -0.105, 0.43, 1.4);
}
.btn > span::after {
  content: "";
  background-color: #4a8826;
  width: 2px;
  height: 70%;
  position: absolute;
  top: 15%;
  right: -1px;
}
.btn > .icon {
  width: 28%;
  right: 0;
  transition: all 0.2s cubic-bezier(0.31, -0.105, 0.43, 1.4);
}

.btn > .icon > .fa {
  font-size: 30px;
  vertical-align: middle;
  transition: all 0.2s ease;
}

.btn > .icon > .fa-remove {
  height: 36px;
}

.btn > .icon > .fa-check {
  display: none;
}

.btn > .success > span,
.btn:hover > span {
  left: -72%;
  opacity: 0;
}

.btn > .success > .icon,
.btn:hover > .icon {
  width: 100%;
}

.btn > .success > .icon > .fa,
.btn:hover > .icon > .fa {
  font-size: 45px;
}

.btn > .success > .icon > .fa-remove {
  display: none;
}
.btn > .success > .icon > .fa-check {
  display: inline-block;
}

.btn:hover {
  opacity: 0.9;
}
.btn:hover > .icon > .fa-remove {
  height: 45px;
}
.btn:active {
  opacity: 1;
}
</style>

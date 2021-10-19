<template>
  <div class="button-wrapper">
    <button :class="'button-body' + ' ' + this.buttonStyle">
      <p class="button-text">
        {{ buttonText }}
      </p>
    </button>
  </div>
</template>

<script>
export default {
  props: {
    buttonText: String,
    buttonStyle: String
  }
};
</script>

<style>
.button-body {
  transition: background-color 0.1s, box-shadow 0.1s;
  cursor: pointer;
  font-size: 14px;
  padding: 0.5em 1em;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.1);
}
.button-body.normal {
  background-color: #f6f6f6;
  color: #3d2c8d;
}
.button-body.normal:hover {
  background-color: #f0f0f0;
}
.button-body.normal:active {
  background-color: #e8e8e8;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
}
.button-body.important {
  color: #f6f6f6;
  border: 1px solid rgba(255, 255, 255, 0.1);
  background-color: #3d2c8d;
}
.button-body.important:hover {
  background-color: #44309c;
}
.button-body.important:active {
  background-color: #453595;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
}
</style>

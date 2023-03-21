<template>
  <div
      class="popup"
  >
    <span
        @click="closePopup()"
        class="close">
      X
    </span>
    <p class="title__popup">
      Комплект {{cartMats.view}}
      <span class="span">{{cartMats.price}}</span>
    </p>
    <img class="img__popup" :src="cartMats.imgPopup" alt="images">
    <p class="check">
      {{cartMats.textPopup1}}
    </p>
    <p class="check">
      {{cartMats.textPopup2}}
    </p>
    <p class="check">
      {{cartMats.textPopup3}}
    </p>
    <p class="check">
      {{cartMats.textPopup4}}
    </p>
    <p class="check">
      {{cartMats.textPopup5}}
    </p>
  </div>
</template>
<script>

export default {
  name: "App",

  data() {
    return {
    }
  },

  props: {
    cartMats: {
      type: Object,
      required: true
    },
  },

  emits: ["closePopup"],

  methods: {
    closePopup() {
      this.$emit("closePopup");
    }
  }
};

</script>

<style>
.check{
  margin-top: 10px;
  margin-bottom: 10px;
  position: relative;
  font-size: 20px;
  font-weight: 500;
}
.popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  width: 600px;
  display: block;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  z-index: 1000;
}
.img__popup{
  width: 100%;
  max-width: 600px;
}

.span{
  color: #d20004;
}
.title__popup{
  font-size: 25px;
  font-weight: 700;
  margin-bottom: 20px;
}
.close{
  position: absolute;
  top: 20px;
  right: 20px;
  cursor: pointer;
}
</style>

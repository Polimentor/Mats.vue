<template>
  <div class="container">
    <div class="wrapper">
      <div class="box">
        <p class="title">
          Крок 2 із 4
        </p>
        <strong  class="description">
          Наступний крок - персоналізація, підбір кольорової гами <br>
          Ваших майбутніх килимків
        </strong>
        <select
            class="select"
            v-model="selectedMats"
        >
          <option
              selected
              disabled
              :value="{value:'black'}"
          >
            Колір полімера</option>
          <option
              class="option"
              v-for="mat in colorsMats"
              :key="mat.value"
              :value="mat"
          >
            {{mat.name}}
          </option>
        </select>
        <select
            class="select"
            v-model="selectedEdging"
        >
          <option
              selected
              disabled
              :value="{value:'black'}"
          >Колір канта</option>
          <option
              v-for="edging in colorsEdging"
              :key="edging.value"
              :value="edging"
          >
            {{edging.name}}
          </option>
        </select>
        <div class="btn__group">
          <button
              class="button__prev"
              @click="backMats"
          >
            Повернутися Назад
          </button>
          <button
              class="button__next"
              @click="submitColor()"
          >
            Далі
          </button>
        </div>
      </div>
      <div class="img">
        <ImagesColorsMats :colorBorder="selectedEdging.value" :colorMat="selectedMats.value"/>
      </div>
    </div>
  </div>
</template>
<script>

import ImagesColorsMats from "@/components/ImagesColorsMats.vue";
export default {
  name: "App",

  components: {
    ImagesColorsMats
  },

  data() {
    return {
      colorsMats: [
        {value: 'red', name: 'червоний'},
        {value: 'blue', name: 'синий'},
        {value: 'yellow', name: 'желтый'},
        {value: 'green', name: 'зеленый'},
        {value: 'orange', name: 'оранжевый'},
        {value: 'purple', name: 'фиолетовый'},
        {value: 'pink', name: 'розовый'},
        {value: 'grey', name: 'серый'},
        {value: 'black', name: 'черный'},
        {value: 'white', name: 'белый'}
      ],
      selectedMats: {value: 'black' },
      colorsEdging: [
        {value: 'green', name: 'хаки'},
        {value: 'lavender', name: 'лавандовый'},
        {value: 'yellow', name: 'желтый'},
        {value: 'green', name: 'зеленый'},
        {value: 'orange', name: 'оранжевый'},
        {value: 'purple', name: 'пурпуровый'},
        {value: 'pink', name: 'розовый'},
        {value: 'grey', name: 'серый'},
        {value: 'black', name: 'черный'},
        {value: 'white', name: 'белый'}
      ],
      selectedEdging: {value: 'black'},
      selectedСolors: [],
      currentMats: 0
    }
  },

  emits: ["stepMats", "backMats"],

  methods: {
    submitColor() {
      if (this.selectedMats && this.selectedEdging) {
       this.selectedСolors.Mats = this.selectedMats;
       this.selectedСolors.Edging = this.selectedEdging;
       this.$emit("stepMats")
       console.log(this.selectedСolors)
      }
    },

    backMats(){
      this.$emit("backMats")
    }
  }
}
</script>

<style >

  .btn__group{
    display: flex;
    margin-top: 30px;
  }
  .button__prev{
    font-size: 18px;
    color: #999;
    text-transform: uppercase;
    display: block;
    background: none;
    border: 0;
    padding: 0;
    cursor: pointer;
    outline: none;
    background: #fff;
    border: 1px solid #999;
    border-radius: 4px;
    padding: 15px;
    margin-right: 20px;
  }
  .button__next{
    outline: none;
    font-size: 18px;
    letter-spacing: 1.2px;
    font-weight: 700;
    margin: 0;
    padding: 12px 0;
    cursor: pointer;
    user-select: none;
    color: #fff;
    border: 1px solid #d20004;
    border-radius: 4px;
    padding: 15px;
    background: #d20004;
    text-transform: capitalize;
    display: block;
  }
</style>
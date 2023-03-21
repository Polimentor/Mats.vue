<template>
  <div class="container">
    <div
        v-if="currentForm === 1"
    >
      <p class="title">
        Крок 4 із 4
      </p>
      <h3 class="description">
        Последний шаг – определение сроков пошива и одного из 4 <br>
        способов оплаты. Заполните форму для связи с консультантом
      </h3>
      <form class="form">
        <div class="form_group">
          <input
              class="input"
              type="name"
              placeholder="Ім'я"
              v-model="name"
          >
          <input
              class="input"
              placeholder="Телефон"
              pattern="^380\d{9}$"
              maxlength="12"
              v-model="telephone"
          >
        </div>
        <div>
          <input class="checkbox" type="checkbox">
          <label class="label">Даю згоду на обробку персональних даних</label>
        </div>
        <div class="btn-group">
          <button
              class="button__prev"
              @click="backMats()"
          >Повернутися назад</button>
          <button
              class="button"
              @click="submitFromData()"
          >
            Чекаю дзвінка</button>
        </div>
      </form>
    </div>
      <div v-else>
        <div class="text__end">
          <p class="button button__size">
            Дякую за замовлення, {{formData.name}}
          </p>
        </div>
        <p class="description">
          Ми зв'яжемося з вами найближчим часом, щоб обговорити килимки,<br>
          які вже чекають на ваш автомобіль
        </p>
      </div>
    </div>
</template>
<script>

export default {
  name: "App",

  data() {
    return{
      name: [],
      telephone: [],
      formData: [],
      currentForm: 1
    }
  },

  props: {
    markName: {
      type: Object,
      default: "black"
    }
  },

  emits: ["backMats"],

  methods:{
    backMats(){
      this.$emit("backMats")
    },

    submitFromData() {
      if ( this.name && this.telephone) {
        this.formData.name = this.name;
        this.formData.telephone = this.telephone;
        this.currentForm = 2
        console.log(this.formData);
      }
    },
  }


}
</script>

<style>
  .input{
    width: 100%;
    max-width: 500px;
    margin-bottom: 20px;
    border: 1px solid rgb(204, 204, 204);
    border-radius: 4px;
    padding: 0px 15px;
    display: flex;
    height: 50px;
    font-size: 15px;
    align-items: center;
    outline: none;
    box-shadow: none;
    appearance: none;
  }
  .btn-group{
    display: flex;
    margin-top: 20px;
  }
  .label{
    font-size: 18px;
    font-weight: 600;
  }
  .checkbox{
    width: 15px;
    height: 15px;
  }
  .form {
    margin-top: 20px;
  }
  .text__end{
    display: flex;
    justify-content: start;
    margin-top: 10vw;
    margin-bottom: 1vw;
  }
  .button__size{
    font-size: 20px;
  }
</style>
<template>
  <div class="container">
    <Popup
        v-if="showPopup"
        :cartMats="filteredCarMats"
        :showPopup="showPopup"
        @closePopup="showPopup = 0"
    />
    <div>
      <h2 class="title">
        Крок 3 із 4
      </h2>
      <h3 class="description">
        Наступний крок - вибір комплекту та добір додаткових аксесуарів
      </h3>
    </div>
    <div class="carts">
      <div
          class="cart"
          v-for="cart in cartMats"
          :key="cart"
      >
        <div class="view__box">
          <p>
            {{cart.view}}
          </p>
          <img
              @click="openPopup(cart.view)"
              class="icon__cart"
              :src="cart.icon"
              alt="images"
          >
        </div>
        <img
            class="img"
            :src="cart.img"
            alt="images"
        >
        <div class="checkbox__group">
          <div class="box__2">
            <input class="checkbox" type="checkbox">
            <label class="info1" >Подпятник</label>
              <img
                  class="img__icon" src="https://www.freeiconspng.com/uploads/fichier-info-icon-002-svg---wikip-dia-28.png" width="15" alt="Fichier:Info icon 002 svg — Wikipédia"
              />
          </div>
          <div class="box__2">
            <input class="checkbox" type="checkbox">
            <label class="info1" >Шильди</label>
              <img
                  class="img__icon" src="https://www.freeiconspng.com/uploads/fichier-info-icon-002-svg---wikip-dia-28.png" width="15" alt="Fichier:Info icon 002 svg — Wikipédia"
              />
          </div>
        </div>
        <p class="total">
          Разом
        </p>
        <p
           class="price"
        >
           {{cart.price}} грн
        </p>
        <button
            class="button"
            @click="stepMats()"
        >
          Вибрати
        </button>
      </div>
    </div>
    <button
        class="button__prev btn__margin"
        @click="backMats()"
    >
      Повернутися назад
    </button>
  </div>
</template>
<script>

import Popup from '@/components/Popup.vue'
export default {
  name: "App",

  components: {
    Popup
  },

  data() {
    return{
      showPopup: 0,
      selectedModel: "",
      cartMats:[
        {
          img:"https://cdn.evakovrik.in.ua/241022R1/img/premiumBagazhnik.036e28e7.jpg",
          view: "Економ",
          icon: "https://www.freeiconspng.com/uploads/fichier-info-icon-002-svg---wikip-dia-28.png",
          price: "1200",
          imgPopup: "https://cdn.evakovrik.in.ua/241022R1/img/bagaj.583f17ba.jpg",
          titlePopup: "Комплект Багажник",
          textPopup1: "Передние или задние с перемычкой",
          textPopup2: "Гарантия от 6 до 12 мес",
          textPopup3: "Срок пошива 5-7 дней",
          textPopup4: "Оригинальные крепления + система липучек",
          textPopup5: "Пакет документов"
        },
         {
           img:"https://cdn.evakovrik.in.ua/241022R1/img/premium.66617c8b.jpg",
           view: "Стандарт",
           icon: "https://www.freeiconspng.com/uploads/fichier-info-icon-002-svg---wikip-dia-28.png",
           price: "1300",
           imgPopup: "https://cdn.evakovrik.in.ua/241022R1/img/bagaj.583f17ba.jpg",
           titlePopup: "Комплект Багажник",
           textPopup1: "Передние или задние с перемычкой",
           textPopup2: "Гарантия от 6 до 12 мес",
           textPopup3: "Срок пошива 5-7 дней",
           textPopup4: "Оригинальные крепления + система липучек",
           textPopup5: "Пакет документов"
         },
         {
           img:"https://cdn.evakovrik.in.ua/241022R1/img/vip.d45e1651.jpg",
           view: "Багажник ",
           icon: "https://www.freeiconspng.com/uploads/fichier-info-icon-002-svg---wikip-dia-28.png",
           price: "1200",
           imgPopup: "https://cdn.evakovrik.in.ua/241022R1/img/bagaj.583f17ba.jpg",
           titlePopup: "Комплект Багажник",
           textPopup1: "Передние или задние с перемычкой",
           textPopup2: "Гарантия от 6 до 12 мес",
           textPopup3: "Срок пошива 5-7 дней",
           textPopup4: "Оригинальные крепления + система липучек",
           textPopup5: "Пакет документов"
        },
        {
           img:"https://cdn.evakovrik.in.ua/241022R1/img/premium.66617c8b.jpg",
           view: "Премиум (багажник)",
           icon: "https://www.freeiconspng.com/uploads/fichier-info-icon-002-svg---wikip-dia-28.png",
           price: "1600",
           imgPopup: "https://cdn.evakovrik.in.ua/241022R1/img/bagaj.583f17ba.jpg",
           titlePopup: "Комплект Багажник",
           textPopup1: "Передние или задние с перемычкой",
           textPopup2: "Гарантия от 6 до 12 мес",
           textPopup3: "Срок пошива 5-7 дней",
           textPopup4: "Оригинальные крепления + система липучек",
           textPopup5: "Пакет документов"
        },
        {
           img:"https://cdn.evakovrik.in.ua/241022R1/img/standart.79e6f319.jpg",
           view: "Премиум ",
           icon: "https://www.freeiconspng.com/uploads/fichier-info-icon-002-svg---wikip-dia-28.png",
           price: "1800",
           imgPopup: "https://cdn.evakovrik.in.ua/241022R1/img/bagaj.583f17ba.jpg",
           titlePopup: "Комплект Багажник",
           textPopup1: "Передние или задние с перемычкой",
           textPopup2: "Гарантия от 6 до 12 мес",
           textPopup3: "Срок пошива 5-7 дней",
           textPopup4: "Оригинальные крепления + система липучек",
           textPopup5: "Пакет документов"
        },
        {
           img:"https://cdn.evakovrik.in.ua/241022R1/img/premium.66617c8b.jpg",
           view: "VIP",
           icon: "https://www.freeiconspng.com/uploads/fichier-info-icon-002-svg---wikip-dia-28.png",
           price: "12200",
           imgPopup: "https://cdn.evakovrik.in.ua/241022R1/img/bagaj.583f17ba.jpg",
           titlePopup: "Комплект Багажник",
           textPopup1: "Передние или задние с перемычкой",
           textPopup2: "Гарантия от 6 до 12 мес",
           textPopup: "Срок пошива 5-7 дней",
           textPopup4: "Оригинальные крепления + система липучек",
           textPopup5: "Пакет документов"
        },
      ],
    }
  },

  emits: ["stepMats","backMats"],

  computed: {
    filteredCarMats(){
      return this.cartMats.find(i => i.view === this.selectedModel)
    }
  },

  methods: {

    stepMats(){
      this.$emit("stepMats")
    },

    backMats(){
      this.$emit("backMats")
    },

    openPopup(model){
      this.showPopup = 1
      this.selectedModel = model
    }
  }
}
</script>

<style>
 .carts{
   display: flex;
   flex-wrap: wrap;
   margin-top: 20px;
 }
 .cart{
   margin-top: 20px;
   margin-right: 20px;
   padding: 20px;
   box-shadow: 1px 1px  9px 1px  #a8a8a8;
   box-sizing: border-box;
   border: 1px solid transparent;
   transition: border-color 0.3s ease-in-out;
   cursor: pointer;
 }
 .cart:hover{
   border-color: #d20004;
 }
 .img{
   width: 100%;
   max-width: 270px;
 }
 .price{
   font-size: 20px;
   margin-bottom: 20px;
 }
 .btn__margin{
   margin-top: 20px;
   margin-bottom: 100px;
 }
 .total{
   font-size: 16px;
   color: #a8a8a8;
   margin-top: 20px;
 }
 .box__2{
   display: flex;
   align-items: center;
 }
 .img__icon{
   margin-left: 10px;
 }
 .info1{
   margin-left: 10px;
 }
 .checkbox__group{
   margin-top: 20px;
 }
 .view__box{
   display: flex;
 }
 .icon__cart{
   width: 20px;
   margin-left: 5px;
 }
</style>
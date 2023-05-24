<template>
    <div class="section__step__content _container">
      <div class="progress-wrap">
        <div class="progress" id="progress"></div>
        <div class="step active">01</div>
        <div class="step">02</div>
        <div class="step">03</div>
      </div>
    </div>
    <!-- <button class="btn" id="prev" @click="prevClick" disabled>Prev</button>
    <button class="btn" id="next" @click="nextClick">Next</button> -->

    <div class="section__step__items">
      <div v-if="currentStep===1">
        <div class="section__step__item">
            <img src="../assets/form-icon.png" alt="">
            <div class="section__step__item__title">Заполнение формы</div>
            <div class="section__step__item__text">Первым шагом в процессе выпуска карты является заполнение простой и удобной онлайн-формы. Вам потребуется предоставить некоторую информацию, необходимую для обработки вашего запроса.</div>
          </div>
      </div>
      <div v-if="currentStep===2">
        <div class="section__step__item">
            <img src="../assets/qr-icon.png" alt="">
            <div class="section__step__item__title">Оплата с картой или QR</div>
            <div class="section__step__item__text">После заполнения формы вы будете перенаправлены на страницу оплаты. Вы можете выбрать удобный способ оплаты, включая оплату с помощью вашей существующей карты или с помощью QR-кода.</div>
          </div>
      </div>
      <div v-if="currentStep===3">
        <div class="section__step__item">
            <img src="../assets/card-icon.png" alt="">
            <div class="section__step__item__title">Ждите карту</div>
            <div class="section__step__item__text">После успешной оплаты и обработки заказа, вам останется только дождаться доставки карты в вашу организацию. Обеспечим быструю и надежную доставку вашей карты, чтобы вы могли начать использовать ее в кратчайшие сроки.</div>
          </div>
      </div>

      <button class="section__step__items__arrow prev__arrow" id="prev" @click="prevClick" disabled><img src="../assets/left-arrow.png" alt=""></button>
      <button class="section__step__items__arrow next__arrow" id="next" @click="nextClick"><img src="../assets/left-arrow.png" alt=""></button>
    </div>
    
 </template>
 <script>
 
 export default {
   components: {

   },
   data(){
    return{
      currentStep:1
    }
   },
   methods:{
    nextClick(){
      let steps = document.querySelectorAll(".step");
      this.currentStep++;
        if (this.currentStep > steps.length) {
          this.currentStep = steps.length;
        }
        this.update();
    },
    prevClick(){
      this.currentStep--;
        if (this.currentStep < 1) {
          this.currentStep = 1;
        }
        this.update();
    },
    update() {
        const prev = document.getElementById("prev");
        const next = document.getElementById("next");
      let progress = document.getElementById("progress");
      let steps = document.querySelectorAll(".step");
      steps.forEach((step, i) => {
        if (i < this.currentStep) {
          step.classList.add("active");
        } else {
          step.classList.remove("active");
        }
      });

      let activeSteps = document.querySelectorAll(".active");

      progress.style.width =
        ((activeSteps.length - 1) / (steps.length - 1)) * 100 + "%";

      if (this.currentStep === 1) {
        prev.disabled = true;
      } else if (this.currentStep === steps.length) {
        next.disabled = true;
      } else {
        next.disabled = false;
        prev.disabled = false;
      }
    }

   }
 };
 </script>
 


 <style lang="scss">
 @font-face {
  font-family: 'SF Pro Display Bold';
  src: url('../assets/fonts/SFPRODISPLAYBOLD.OTF') format('opentype');
  font-weight: 700;
  font-weight: normal;
}

$regular: 'SF Pro Display Regular', sans-serif;
$meduim: 'SF Pro Display Medium', sans-serif;
$bold: 'SF Pro Display Bold', sans-serif;
.container {
  text-align: center;
}

.progress-wrap {
  max-width: 870px;
  margin: 0 auto;
  margin-bottom: 40px;
  position: relative;
  display: flex;
  justify-content: space-between;
  @media screen and (max-width: 479.98px) {
    margin-bottom: 0px;
  }
  &:before {
    content: "";
    width: 100%;
    height: 1px;
    position: absolute;
    top: 50%;
    left: 0;
    transform: translateY(-50%);
    z-index: -1;
    transition: 0.3s ease-in-out;
    background-image:linear-gradient(to right, #AAAAAA 0%, #AAAAAA 50%, transparent 50%);
    background-size:20px 1px;
    background-repeat:repeat-x;
  }
}


.progress {
  width: 0;
  height: 0px;
  border:1px solid #2176FF;
  position: absolute;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
  z-index: -1;
  transition: 0.3s ease-in-out;
}

.step {
  font-family: $bold;
  width: 70px;
  height: 70px;
  font-weight: 700;
  font-size: 28px;
  line-height: 33px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #AAAAAA;
  background-color: #fff;
  border: 2px solid #e6e6e6;
  border-radius: 50%;
  transition: 0.3s ease-in-out;
  @media screen and (max-width: 479.98px) {
    width: 50px;
    height: 50px;
  }
}

.step.active {
  color:#ffffff;
  border: none;
  background: linear-gradient(180deg, #2176FF 0%, #33A1FD 100%);
}

.section__step__items{
  position: relative;
  @media screen and (max-width: 1180px) {
      margin: 0 auto;
      width: 500px;
    }
    @media screen and (max-width: 479.98px) {
      width: 100%;
      padding: 20px;
    }
  &__arrow{
    position: absolute;
    top: 50%;
    background: none;
    &:disabled {
      opacity: 0.5;
      pointer-events: none;
    }
  }
  .prev__arrow{
    left: 5px;
  }
  .next__arrow{
    right: 5px;
    transform: rotate(180deg);

  }
}

</style>
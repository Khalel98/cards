<template lang="">
<div class="lb_accordeon" id="lb_accordeon">
  <ul class="lb_accordeon__item">
     <li v-for="(item, index) in faq" class="lb_item" v-on:click="faqTrigger(index)" v-bind:class="{'lb_ext-active': (currentFaq === index)}" :key="index">
      <div class="lb_item__title">
         <div style="display:flex; align-items:center;">
            <div class="edit__icon">
               <svg width="26" height="26" viewBox="0 0 26 26" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M1.39286 24.6072H21.0357M12.1071 18.3572L6.75 19.3215L7.64286 13.8929L19.6607 1.91078C19.8267 1.74341 20.0242 1.61056 20.2418 1.5199C20.4594 1.42924 20.6928 1.38257 20.9286 1.38257C21.1643 1.38257 21.3977 1.42924 21.6153 1.5199C21.8329 1.61056 22.0304 1.74341 22.1964 1.91078L24.0893 3.80364C24.2567 3.96964 24.3895 4.16714 24.4802 4.38475C24.5708 4.60236 24.6175 4.83576 24.6175 5.07149C24.6175 5.30723 24.5708 5.54063 24.4802 5.75824C24.3895 5.97584 24.2567 6.17335 24.0893 6.33935L12.1071 18.3572Z" stroke="#2176FF" stroke-width="1.78571" stroke-linecap="round" stroke-linejoin="round"/>
               </svg>
            </div>
            <h2><span v-html="item.title"></span></h2>
         </div>
        <div class="" :class="currentFaq === index ? 'drop__up' : 'drop__down'">
         <svg width="18" height="11" viewBox="0 0 18 11" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M9.00001 10.4625C8.80001 10.4625 8.60601 10.425 8.41801 10.35C8.23001 10.275 8.07401 10.175 7.95001 10.05L1.05001 3.14995C0.775012 2.87495 0.637512 2.52495 0.637512 2.09995C0.637512 1.67495 0.775012 1.32495 1.05001 1.04995C1.32501 0.774951 1.67501 0.637451 2.10001 0.637451C2.52501 0.637451 2.87501 0.774951 3.15001 1.04995L9.00001 6.89995L14.85 1.04995C15.125 0.774951 15.475 0.637451 15.9 0.637451C16.325 0.637451 16.675 0.774951 16.95 1.04995C17.225 1.32495 17.3625 1.67495 17.3625 2.09995C17.3625 2.52495 17.225 2.87495 16.95 3.14995L10.05 10.05C9.90001 10.2 9.73751 10.3065 9.56251 10.3695C9.38751 10.4325 9.20001 10.4635 9.00001 10.4625Z" fill="#546A7B"/>
         </svg>
        </div>
      </div>
      <transition mode="out-in" name="faq-fade" 
                  v-on:before-enter="beforeEnterFaq"
                  v-on:enter="enterFaq">
        <div class="lb_item__copy" v-show="currentFaq === index">
          <div class="lb_item-copy-ct" v-html="item.copy">
          </div>
        </div>
      </transition>
    </li>
  </ul>
</div>
</template>
<script>
import '@/styles/variables.scss';

export default {
   data: function() {
    return {
      faq: [
        {
          title: 'Как долго займет получение карты?',
            copy:'Мы предлагаем несколько удобных способов оплаты, включая оплату с помощью существующей кредитной карты или использование QR-кода для оплаты через мобильное приложение или платежную систему.'
          },
        {
         title: 'Какую информацию мне нужно предоставить при заполнении формы?',
         copy:'Мы предлагаем несколько удобных способов оплаты, включая оплату с помощью существующей кредитной карты или использование QR-кода для оплаты через мобильное приложение или платежную систему.'
         },
        {
         title: 'Какие способы оплаты доступны?',
         copy:'Мы предлагаем несколько удобных способов оплаты, включая оплату с помощью существующей кредитной карты или использование QR-кода для оплаты через мобильное приложение или платежную систему.'
         },
        {
         title: 'Могу ли я заказать карту для кого-то другого, например, для ребенка или супруга?',
         copy:'Мы предлагаем несколько удобных способов оплаты, включая оплату с помощью существующей кредитной карты или использование QR-кода для оплаты через мобильное приложение или платежную систему.'
         }
      ],
      currentFaq: -10
    }
  },
  methods: {
        faqTrigger: function(newFaq) {
            if (newFaq === this.currentFaq) {
                this.currentFaq = -10
            } else {
                this.currentFaq = newFaq
            }
        },
        beforeEnterFaq: function(_t) {
          _t.style.display = 'block'
          _t.style.maxHeight = null
          _t.myHeight = _t.offsetHeight
          _t.style.maxHeight = 0
          _t.style.display = null
        },
        enterFaq: function(_t) {
          _t.style.maxHeight = _t.myHeight + 'px'
        }
    },
}
</script>
<style lang="scss">
@keyframes accordeonAni {
   0% {
      max-height: 0;
   }
}

.lb_accordeon {
   max-width:1000px;
   margin: 0 auto;
   .lb_item {
      display: block;
      margin-bottom: 10px;
      border: 1px solid #AAAAAA;
      border-radius: 10px;
      &__title {
         position: relative;
         padding: 20px;
         font-size: 24px;
         line-height: 29px;
         color: #000000;
         cursor: pointer;
         transition: color 200ms;
         display: flex;
         justify-content: space-between;
         align-items: center;
         @media screen and (max-width: 479.98px) {
            font-size: 18px;
            line-height: 18px;
         }
         .edit__icon{
            padding-right: 40px;
            @media screen and (max-width: 479.98px) {
               padding-right: 20px;
            }
         }
         .drop__up{
            transition: 0.5s ease-in-out;
            transform: rotate(180deg);
         }
         .drop__down{
            transition: 0.5s ease-in-out;
         }
      }
      &__copy {
         margin: 0;
         padding: 0;
         font-size: 20px;
         line-height: 24px;
         color: #31393C;
         @media screen and (max-width: 479.98px) {
            font-size: 14px;
            line-height: 14px;
         }
      }
      .lb_item-copy-ct {
         margin: 0px 20px;
         border-top: 1px solid #AAAAAA;
         padding: 20px 0;
      }
   }
}

.faq-fade {
    &-enter {
      max-height: 0;
      display: block;
    }
    &-enter-to {
    }
    &-enter-active {
      animation: accordeonAni 400ms ease-out;
      overflow: hidden;
    }
    &-leave {
      display: block;
    }
    &-leave-to {
      display: block;
    }
    &-leave-active {
      animation: accordeonAni 400ms ease-out;
      animation-direction: reverse;
      overflow: hidden;
    }
  }
</style>
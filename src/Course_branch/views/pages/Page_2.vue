<template>
<div>
  <div class="container mb-red">
      <hr class="hr-red mb-orange" />
      <div class="row mb-red">
          <div class="col-lg-12 col-xs-6">
              <h1 class="h1 text-uppercase text-left">Цепная реакция</h1>
          </div>
      </div>
  </div>

  <div class="baloon_large baloon_robot baloon_color-white relative mb-60 mb-xs-45">
    <div class="baloon_middle mb-orange" style="padding-bottom: 0">
      <div class="row middle jf-center">
        <div class="col-lg-6 mb-xs-30">
          <div class="mr-10">
            <p class="text-l text-white mb-pink mb-10 mb-xs-10">
              Из опыта ясно: <span class="text-bold">система не просто компоненты. </span> 
            </p>
            <p class="text-l text-white mb-pink">
              Взаимодействие элементов - уникальные свойства, непредсказуемые из свойств самих элементов.
            </p>
          </div>
        </div>
        <div class="col-lg-6 col-xs-6 order-xs-1 flex">
          <img
              class="center"
              src="/images/pers3.png"
              alt=""
              style="width: 100%"
          />
        </div>
      </div>
    </div>
  </div>

  <div class="container">
    <p class="text-m text-gray-light mb-60 mb-xs-45">пролистайте карусель и ответьте на вопрос</p>
    <div class="slider js-slider mb-60 mb-xs-45">
      <div class="slider__items js-slider-items">
        <div v-for="(slide, index) in slides" :key="index" class="slider__item" v-show="index === currentSlide">
          <div class="row center">
            <div class="col-lg-6">
              <picture class="main-people__charset"> 
                <source media="(max-width: 720px)" :srcset="slide.imageXS" /> 
                <img alt="pic" class="img_center" :src="slide.imageLG" /> 
              </picture>
            </div>
            <div class="col-lg-6 align-center">
              <p class="text-l">{{ slide.text }}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="slider__nav js-slider-nav">
        <input type="submit" class="slider__btn slider__btn_prev" @click="prevSlide">
        <ul class="slider__dots js-slider-dots">
          <li v-for="(slide, index) in slides" :key="index" :class="{ 'active': index === currentSlide }">&nbsp;</li>
        </ul>
        <input type="submit" class="slider__btn slider__btn_next" @click="nextSlide">
      </div>
    </div>

    <div v-if="showQuestion" class="mb-60 mb-xs-45 center">
      <div class="row">
        <div class="col-12">
          <h4 class="mb-30 mb-xs-25">{{ currentQuestion }}</h4>
          <p class="text-s text-gray-light mb-20 mb-xs-25">Выбери один ответ</p>
          <div class="test__answers mb-50 mb-xs-30">
            <div v-for="(ans, index) in answers" :key="index" class="radio">
              <input type="radio" :id="'answer'+(index+1)" v-model="selectedAnswer" :value="ans" :disabled="answered"/>
              <label class="text-m" :for="'answer'+(index+1)">{{ ans }}</label>
            </div>
          </div>
          <div class="col-12 text-center">
            <button v-show="!answered" class="btn btn_border js-btn" @click="acceptAnswer">Принять ответ</button>
          </div>
        </div>
      </div>
    </div>
  </div>
  
  <div v-if="showResult" class="mb-60 mb-xs-45">
    <div class="row col-12 jf-center">
      <div class="bg-rose-gradient br-20">
          <picture> 
            <source media="(max-width: 720px)" srcset="/images/icon-attention.png" /> <img alt="icon" class="img_center mb-20 mb-xs-20" src="/images/icon-attention.png" /> 
          </picture>
          <p class="text-m"><span class="text-bold">Система</span> &mdash; цельная структура и отдельная единица. Свойства системы невозможно свести к свойствам её&nbsp;элементов.
          </p>
      </div>
    </div>
  </div>

</div>
</template>

<script>
export default {
    components: {},
    data() {
        return {
            slides: [
            { imageLG: "/images/img-2-1-lg.png", imageXS: "/images/img-2-1-xs.png", text: "Друг Маруси отодвинул крышку своего домашнего компьютера, чтобы произвести чистку от пыли, и случайно повредил ножку одной из микросхем." },
            { imageLG: "/images/img-2-2-lg.png", imageXS: "/images/img-2-2-xs.png", text: "«Наверное, ничего страшного, она же крошечная, да и целых осталось много», – решил Игнат и не придал этому значения." },
            { imageLG: "/images/img-2-3-lg.png", imageXS: "/images/img-2-3-xs.png", text: "Друг Маруси прикрутил крышку обратно, включил компьютер и с ужасом увидел, что компьютер больше не реагирует на движения мышью и выводит на экран какую-то ерунду." }
          ],
            currentSlide: 0,
            showQuestion: false,
            currentQuestion: "Как ты думаешь, почему друг Маруси так удивился результату своей неудачной уборки?",
            answers: [
              "Друг Маруси не заметил, что сломал деталь.",
              "Друг Маруси не знает, как работает его компьютер.",
              "Друг Маруси не мог предвидеть, на что повлияет поломка крошечной детали в такой сложной системе как компьютер.",
              "Друг Маруси посчитал, что это ненужная деталь и ничего не изменится от её поломки."
            ],
            selectedAnswer: "",
            showResult: false,
            isAnswerCorrect: false,
            answered: false,
        };
    },
    computed: {},
    methods: {
      nextSlide() {
        if (this.currentSlide === this.slides.length - 1) {
          this.showQuestion = true;
          this.currentSlide = 0;
        } else {
          this.currentSlide++;
        }
    },
      prevSlide() {
        if (this.currentSlide === 0) {
        this.currentSlide = this.slides.length - 1;
      } else {
        this.currentSlide--;
      }
    },
      acceptAnswer() {
        this.showResult = true;
        this.answered = true;
      }
    },
};
</script>

<style>
</style>
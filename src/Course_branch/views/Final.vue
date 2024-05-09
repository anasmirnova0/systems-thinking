<template>
<div>
  <div class="container mb-red">
        <hr class="hr-red mb-orange" />
        <div class="row mb-red">
            <div class="col-lg-12 col-xs-6">
                <h1 class="h1 text-uppercase text-left">Резюме</h1>
            </div>
        </div>
    </div>
    <div class="mb-red">
        <div class="baloon_large baloon_robot baloon_color-white relative" >
            <div class="baloon_middle mb-orange" style="padding-bottom: 0">
                <div class="row middle jf-center">
                    <div class="col-lg-6">
                        <div class="mr-10 mb-20">
                            <p class="text-l text-white mb-pink">
                              Системы окружают нас и мы можем выявлять, изучать их и даже предсказывать их поведение. 
                              Повтори основные тезисы модуля, а я, пожалуй, сделаю парочку упражнений на системное мышление, давно не занимался. 
                              До встречи!
                            </p>
                        </div>
                    </div>
                    <div class="col-lg-6 col-xs-6 order-xs-1">
                      <img
                          class="center"
                          src="/images/pers1.png"
                          alt=""
                          style="width: 100%"
                      />
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="container ">
      <div class="row mb-60 mb-xs-45">
        <div class="col-lg-4 mb-xs-15">
          <hr class="border-red mb-20 mb-xs-15">
          <p class="text-m">Системное мышление – это способность анализировать систему, предсказывать её&nbsp;поведение и управлять ею.
          </p>
        </div>
        <div class="col-lg-4 mb-xs-15">
          <hr class="border-red mb-20 mb-xs-15">
          <p class="text-m">Умение мыслить системно – такая&nbsp;же компетенция, как и другие. Её можно освоить путём регулярных упражнений и тренировок.
          </p>
        </div>
        <div class="col-lg-4 mb-xs-15">
          <hr class="border-red mb-20 mb-xs-15">
          <p class="text-m">Системное мышление позволяет нам предвидеть проблемы и готовить их решение заранее, а&nbsp;значит, управлять будущим.
          </p>
        </div>
      </div>
    </div>
    <div class="bg-rose-gradient pt-35 pb-35 pt-xs-35 pb-xs-35 mb-60 mb-xs-30" style="padding: 30px; border-radius: 20px;">
      <div class="col-lg-12">
        <h3 class="text-center">Чтобы завершить курс, закрой окно курса.
        </h3>
      </div>
    </div>
</div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters("status", ["visitTotal", "visit"]),
    getTotalWhatch() {
      return Math.floor((this.visit.length * 100) / this.visitTotal);
    },
  },
  data() {
        return {};
    },
  methods: {
    closeCource() {
      window.close();
    },
  },
};
</script>

<style>
</style>
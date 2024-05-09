<template>
<div>
    <div class="container mb-30 mb-xs-15">
        <hr class="hr-red mb-orange" />
        <div class="row">
            <div class="col-lg-12 col-xs-6">
                <h1 class="h1 text-uppercase text-left">Практическое задание</h1>
            </div>
        </div>
    </div>
    <div class="mb-60 ">
        <div class="baloon_large baloon_robot baloon_color-white relative" v-if="!showTest">
            <div class="baloon_middle mb-orange" style="padding-bottom: 0">
                <div class="row middle jf-center">
                    <div class="col-lg-6 mb-xs-15">
                        <div class="mr-10 mb-20 mb-xs-10">
                            <p class="text-l text-white mb-pink">
                                Чтобы полученные знания лучше усвоились, предлагаю выполнить практическое задание. 
                                Тебе нужно ответить правильно на все вопросы, чтобы завершить модуль. Успехов!
                            </p>
                        </div>
                        <div style="display: flex; justify-content: center;">
                            <router-link class="btn" :to="{ name: 'tutorial-page' }">К Началу</router-link>
                            <button class="btn btn_border js-btn" @click="showTest = true">
                                <span class="btn__text">К тесту</span>
                            </button>                          
                        </div>

                    </div>
                    <div class="col-lg-6 col-xs-6 order-xs-1">
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
    </div>
    <div class="container">
        <div class="test" v-if="showTest">
            <p>{{ $route.params.id }}</p>
            <Testing :question-storage="testing"></Testing>
        </div>
    </div>
</div>
</template>
    
<script>
import { ref } from "vue";
import { keybordData_1, testing_1 } from "&/courseData/testingData";
import Testing from "@/components/Testing.vue";

export default {
  components: {
    Testing,
  },
  setup() {
    const showTest = ref(false);
    const keybord_1 = keybordData_1();
    const testing = testing_1().date;

    return { showTest, keybord_1, testing };
  },
};
</script>

<style>
</style>
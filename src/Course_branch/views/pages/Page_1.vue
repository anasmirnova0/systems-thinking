<template>
<div>
    <div class="container mb-red">
        <hr class="hr-red mb-orange" />
        <div class="row mb-red">
            <div class="col-lg-12 col-xs-6">
                <h1 class="h1 text-uppercase text-left">введение</h1>
            </div>
        </div>
    </div>
    <div class="mb-60 mb-xs-45">
        <div class="baloon_large baloon_robot baloon_color-white relative">
            <div class="baloon_middle mb-orange" style="padding-bottom: 0">
                <div class="row middle jf-center">
                    <div class="col-lg-6">
                        <div class="mr-10">
                            <p class="text-l text-white mb-pink">
                                На этом курсе я передам тебе опыт, который я приобрела за годы практики, и покажу, как интегрировать системное мышление в повседневную жизнь.
                            </p>
                            <p class="text-l text-white">
                                На этом этапе тебе будут представлены <span class="text-bold">основные принципы системного подхода.</span>
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
    <div class="container mb-60 mb-xs-45 js-checkbox-items">
        <div class="row">
            <div class="col-12 mb-60 mb-xs-45">
                <h3 class="mb-20 mb-xs-15">На что ты хочешь в первую очередь сосредоточить свое внимание?</h3>
                <p class="text-m text-gray-light">выберите один или несколько вариантов из предложенных</p>
            </div>
            <div class="col-12 mb-20 mb-xs-20 checkbox-puzzle__container">
                <div class="checkbox checkbox_puzzle" v-for="(item, index) in items" :key="index">
                    <input :id="'c' + (index + 1)" type="checkbox" v-model="selectedItems" :value="item.id" />
                    <label :for="'c' + (index + 1)" class="text-m">{{ item.label }}</label>
                </div>
            </div>
            <div class="col-12 text-center">
                <button class="btn btn_border js-btn" v-show="selectedItems.length > 0">
                    <span class="btn__text">Принять ответ</span>
                </button>
            </div>
        </div>
    </div>
    <div class="container mb-150 mb-xs-45 js-hide-content" v-show="showHideContent">
        <div class="row jf-center mb-100 mb-xs-45">
            <div class="col-lg-5 col-xs-6" style="display: flex; justify-content: end;">
                <img
                    class="robot-dialog_img-hide"
                    src="/images/pers_male_1.png"
                    alt=""
                    style="width: 40%; position: relative; top: 90px;"
                />
            </div>
            <div class="col-lg-5 col-xs-6">
                <div class="robot-dialog_baloon mb-xs-20 text-m">
                    Удели особое внимание наиболее интересным для тебя темам.
                </div>
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
            items: [
                { id: 'c1', label: 'Что представляет собой система и системное мышление?' },
                { id: 'c2', label: 'Какие типы систем могут быть выделены?' },
                { id: 'c3', label: 'Каким образом формулировать вопросы с системным подходом?' },
                { id: 'c4', label: 'Возможно ли обучиться системному мышлению?' },
                { id: 'c5', label: 'Какие задачи решаются с помощью систем?' },
                { id: 'c6', label: 'Зачем применять системное мышление?' },
                { id: 'c7', label: 'Ни на что из перечисленного.' }
            ],
            selectedItems: [],
            showHideContent: false
        };
    },
    computed: {},
    mounted() {
        const btn = document.querySelector('.js-btn');
        const inputs = document.querySelectorAll('.js-checkbox-items input');

        inputs.forEach(input => {
        input.addEventListener('click', () => {
            const inputChecked = document.querySelectorAll('.js-checkbox-items input:checked').length;
            btn.style.display = inputChecked > 0 ? '' : 'none';
        });
        });

        btn.addEventListener('click', () => {
        btn.style.display = 'none';
        this.showHideContent = true;
        inputs.forEach(input => {
            input.disabled = true;
        });
        });
    },
};
</script>

<style>
</style>
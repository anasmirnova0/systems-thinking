<template>
    <div class="splash">
        <div class="container-full">
            <div class="row splash-container h-100">
                <div class="splash-container-flex">
                    <div class="col-lg-5 bottom splash-container-order" style="
                    display: flex;
                    flex-direction: column;
                ">
                 
                            <p class="text-violet text-uppercase">Электронный курс (демо версия)</p>
                            <h1 class="splash-title mb-40 mb-xs-40">Системное мышление</h1>
                            <h4 class="mb-40 mb-xs-40">Эффективное решение<br/>задач с помощью<br/>системного мышления</h4>
                            <router-link
                                    :to="{ name: 'tutorial-page' }"
                                    @click="getStart"
                                    class="btn splash-btn"
                                >
                                    <span>Начать</span
                                    ><SvgIcon
                                        name="next"
                                        w="50"
                                        h="20"
                                        color="white"
                                    ></SvgIcon>
                            </router-link>
                
                    </div>
                    <div class="col-lg-5 bottom">
                        <picture> 
                            <source class="splash_bg " media="(max-width: 720px)" srcset="/images/splash-xs.png" /> <img alt="icon" class="splash_bg" src="/images/splash-lg.png" /> 
                        </picture>
                    </div>
                </div>
            </div>
        </div>
    </div> 
</template>

<script>
import { mapActions, mapGetters } from "vuex";
import SvgIcon from "@/components/ui/SvgIcon.vue";
export default {
    components: {
        SvgIcon,
    },
    computed: {
        ...mapGetters("status", ["start"]),
    },
    methods: {
        ...mapActions("status", ["getStart"]),
    },
};
</script>

<style lang="scss">
</style>
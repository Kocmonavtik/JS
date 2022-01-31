<template>
    <transition name="fade">
        <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" v-if="info.VisibleResume">
            <div class="grid grid-rows-1 grid-cols-5 gap-4 pb-8">
                <div class="col-span-2">
                    <p class="flex items-center text-3xl">{{info.FirstName}} {{info.SecondName}}</p>
                    <p class="flex items-center text-sm pb-4">{{Years}} {{Word}}. Дата рождения: {{info.Birthday}}</p>
                    <p class="flex items-center text-lg">Контакты</p>
                    <p class="flex items-center text-sm ">+7{{info.PhoneNumber}}</p>
                    <p class="flex items-center text-sm pb-4">{{info.Email}}</p>
                    <p class="flex items-center text-lg">Место проживания: {{info.LocationUser}}</p>
                </div>
                <div class="row-span-1 col-span-3">
                    <div class="flex flex-wrap justify-center">
                        <div class="w-full sm:w-6/12 px-4">
                            <img
                                    :src= "info.Image"
                                    alt="..."
                                    class="shadow-xl rounded-full max-w-full h-auto align-middle border-none"/>
                        </div>
                    </div>
                </div>
            </div>

            <div class="grid grid-rows-1 grid-cols-5 gap-4 pb-4">
                <div class="col-span-3">
                    <div v-for="(Edu, index) in info.Education" class="pb-2">
                        <p class="text-left text-2xl pb-4">{{info.Education[index].classEdu}} образование</p>
                        <div v-if="info.Education[index].classEdu !='Среднее'">
                            <p class="text-left text-lg">Учебное заведение: {{info.Education[index].EduInstitution}}</p>
                            <p class="text-left text-sm">Факультет: {{info.Education[index].Faculty}}</p>
                            <p class="text-left text-sm ">Специализация: {{info.Education[index].Specialization}}</p>
                            <p class="text-left text-sm pb-4">Год окончения: {{info.Education[index].YearEnd}}</p>
                        </div>
                    </div>
                    <p class="text-left text-lg">Ключевые навыки</p>
                    <p class="text-left text-sm pb-4">{{info.KeySkills}}</p>
                    <p class="text-left text-lg">О себе</p>
                    <p class="text-left text-sm">{{info.AboutMe}}</p>
                </div>
                <div class="row-span-1 col-span-2">
                    <p class="text-right text-2xl "> Желаемая зарплата</p>
                    <p class="text-right text-2xl " >{{info.Salary}} {{info.Currency}}</p>
                </div>
            </div>

        </form>
    </transition>
</template>

<script>
    export default {
        name: "OutputForm",
        props: {
            info: Object
        },
        computed: {
            Years: {
                get:function () {
                    let now= new Date();
                    let old=new Date(this.info.Birthday.replace('/(\d{4})\.(\d{2})\.(\d{2})/)','$1-$2-$3'));
                    let year=new Date(now - old)
                    return year.getUTCFullYear()-1970;
                }
            },
            Word: {
                get:function () {
                    var txt;
                    var count = this.Years % 100;
                    if (count >= 5 && count <= 20) {
                        txt = 'лет';
                    } else {
                        count = count % 10;
                        if (count == 1) {
                            txt = 'год';
                        } else if (count >= 2 && count <= 4) {
                            txt = 'года';
                        } else {
                            txt = 'лет';
                        }
                    }
                    return txt
                }
            },
        }
    }
</script>

<style scoped>
    .fade-enter-active, .fade-leave-active {
        transition: opacity .4s;
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */
    {
        opacity: 0;
    }
</style>

<template>
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
        <div class="grid grid-rows-1 grid-cols-5 gap-4 pb-1">
            <div class="col-span-2">
                <p class="flex items-center text-lg">Ссылка на фото</p>
                <textarea class="form-textarea shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                          v-model="info.Image"></textarea>
            </div>
            <div class="row-span-1 col-span-3">
                <div class="flex flex-wrap justify-center">
                    <div class="w-full sm:w-6/12 px-4">
                        <img
                                :src= "info.Image"
                                alt="..."
                                class="shadow-xl rounded-full max-w-full h-auto align-middle border-none">
                    </div>
                </div>
            </div>
        </div>


        <p class="text-2xl flex flex-row pb-4">Контактные данные</p>
        <div class="grid grid-cols-3 gap-4 pb-3">
            <p class="flex items-center text-lg">Имя</p>
            <div class="col-span-2">
                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                       v-model="info.FirstName">
            </div>
        </div>


        <div class="grid grid-cols-3 gap-4 pb-8">
            <p class="flex items-center text-lg">Фамилия</p>
            <div class="col-span-2">
                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                       v-model="info.SecondName">
            </div>
        </div>


        <div class="grid grid-cols-3 gap-4 pb-3">
            <p class="flex items-center text-lg">Мобильный телефон</p>
            <div class="col-span-2">
                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                       v-model="info.PhoneNumber"  @blur="info.isPhoneTouched = true" v-bind:placeholder='9770888552'>
            </div>
        </div>


        <transition name="fade">
            <div class="pb-3" v-if="isPhoneError">
                <p class="text-lg text-red-500">Неверный формат номера телефона</p>
            </div>
        </transition>


        <div class="grid grid-cols-3 gap-4 pb-3">
            <p class="flex items-center text-lg">Email</p>
            <div class="col-span-2">
                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                       v-model="info.Email">
            </div>
        </div>


        <div class="grid grid-cols-3 gap-4 pb-8">
            <p class="flex items-center text-lg">Город проживания</p>
            <div class="col-span-2">
                <div class="relative inline-block w-full text-gray-700">
                    <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                           v-model="info.LocationUser" v-on:input="onInputLocation" v-on:change="onChangeLocation" list="dataLocation">
                    <datalist id="dataLocation">
                        <option v-for="item of info.VkCity" :value="item.title" :key="item.id"></option>
                    </datalist>
                </div>
            </div>
        </div>


        <p class="text-2xl flex flex-row pb-4">Основная информация</p>
        <div class="grid grid-cols-3 gap-4 pb-3">
            <p class="flex items-center text-lg">Дата рождения</p>
            <div class="col-span-2">
                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                       type="date" v-model="info.Birthday">
            </div>
        </div>


        <div class="grid grid-cols-3 gap-4 pb-3">
            <p class="flex items-center text-lg">Желаемая зарплата</p>
            <div class="col-span-2 grid grid-cols-5 gap-4">
                <div class="col-span-4 ">
                    <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                           v-model="info.Salary" >
                </div>
                <div class="relative inline-block w-full text-gray-700">
                    <select class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                            v-model="info.Currency">
                        <option>Руб</option>
                        <option>USD</option>
                        <option>EUR</option>
                    </select>
                    <div class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none">
                        <svg class="w-4 h-4 fill-current" viewBox="0 0 20 20">
                            <path d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                  clip-rule="evenodd"
                                  fill-rule="evenodd">
                            </path>
                        </svg>
                    </div>
                </div>
            </div>
        </div>



        <div v-for="(Edu, index) in info.Education" class="pb-2">
            <div class="flex justify-end pb-2" v-if="info.Education.length-1==index && index!=0">
                <button v-on:click="info.Education.splice(index,1)"><img src="./cross.png" width="25" height="25"/></button>
            </div>
            <div class="shadow-md rounded pb-4 bg-gray-100 ">
                <div class="grid grid-cols-3 gap-4 pt-2">
                    <p class="flex items-center text-lg">Образование</p>
                    <div class="col-span-2">
                        <div class="relative inline-block w-full text-gray-700">
                            <select class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                                    v-on:change="onChange"
                                    v-model="info.Education[index].classEdu">
                                <option value="Среднее">Среднее</option>
                                <option value="Среднее специальное">Среднее специальное</option>
                                <option value="Неоконченное высшее">Неоконченное высшее</option>
                                <option value="Высшее">Высшее</option>
                            </select>
                            <div class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none">
                                <svg class="w-4 h-4 fill-current" viewBox="0 0 20 20">
                                    <path d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                          clip-rule="evenodd" fill-rule="evenodd">
                                    </path>
                                </svg>
                            </div>
                        </div>
                    </div>
                </div>


                <transition name="fade">
                    <div v-if="info.Education[index].classEdu !='Среднее'">
                        <div class="grid grid-cols-3 gap-4 pt-3 pb-3">
                            <p class="flex items-center text-lg">Учебное заведение</p>
                            <div class="col-span-2">
                                <div class="relative inline-block w-full text-gray-700">
                                    <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                                           v-model="info.Education[index].EduInstitution" v-on:input="onInputUniversities" list="dataUniversities">
                                    <datalist id="dataUniversities">
                                        <option v-for="item of info.VkUniversities" :value="item.title" :key="item.id"></option>
                                    </datalist>
                                </div>
                            </div>
                        </div>
                        <div class="grid grid-cols-3 gap-4 pb-3">
                            <p class="flex items-center text-lg">Факультет</p>
                            <div class="col-span-2">
                                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                                       v-model="info.Education[index].Faculty">
                            </div>
                        </div>
                        <div class="grid grid-cols-3 gap-4 pb-3">
                            <p class="flex items-center text-lg">Специализация</p>
                            <div class="col-span-2">
                                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                                       v-model="info.Education[index].Specialization">
                            </div>
                        </div>
                        <div class="grid grid-cols-3 gap-4 pb-6">
                            <p class="flex items-center text-lg">Год окончания</p>
                            <div class="col-span-2">
                                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                                       v-model="info.Education[index].YearEnd">
                            </div>
                        </div>
                    </div>
                </transition>
            </div>
        </div>

        <div class="flex justify-end pb-2">
            <button  type="button"
                     class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                     v-on:click="info.Education.push({classEdu: 'Среднее', EduInstitution:'', Faculty: '',Specialization: '', YearEnd: ''})">
                Добавить образование
            </button>
        </div>



        <div class="grid grid-cols-3 gap-4 pb-8">
            <p class="flex items-center text-lg">Ключевые навыки</p>
            <div class="col-span-2">
          <textarea class="form-textarea shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                    v-model="info.KeySkills">
          </textarea>

            </div>
        </div>


        <div class="grid grid-cols-3 gap-4 pb-8">
            <p class="flex items-center text-lg">О себе</p>
            <div class="col-span-2">
          <textarea class="form-textarea shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                    v-model="info.AboutMe">

          </textarea>
            </div>
        </div>



        <div class="">
            <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                    type="button" v-on:click="info.VisibleResume = !info.VisibleResume">
                {{ButtonMessage}}
            </button>
        </div>
    </form>
</template>

<script>
    import axios from "axios";

    export default {
        name: "InputForm",
        props: {
            info: Object
        },
        data () {
            return {
                idLocation: '{ "id":, "title":, "important": 1 }',
            }
        },
        methods: {
          onChange(){
              for(let i=0;i<this.info.Education.length;++i){
              if(this.info.Education[i].classEdu=='Среднее') {
                  this.info.Education[i].Faculty = ''
                  this.info.Education[i].EduInstitution = ''
                  this.info.Education[i].Specialization = ''
                  this.info.Education[i].YearEnd = ''
              }
              }
          },
            onInputLocation(){
              axios.get("https://api.vk.com/method/database.getCities?" +
                  "country_id=1&" +
                  "q=" +this.info.LocationUser +
                  "&need_all=1&" +
                  "count=10&" +
                  "access_token=16bd660e592e5759f2a2cdccd3562b4c8613fb4d03cb49ed0012b38f57f4878a9108d6d50d6bc7c6624c9&" +
                  "v=5.131")
                  .then(response=> this.info.VkCity=response.data.response.items);

          },
            onChangeLocation(){
              axios.get('https://api.vk.com/method/database.getCities?' +
                  'country_id=1&' +
                  'q=' + this.info.LocationUser +
                  '&need_all=1&' +
                  'count=1&' +
                  'access_token=16bd660e592e5759f2a2cdccd3562b4c8613fb4d03cb49ed0012b38f57f4878a9108d6d50d6bc7c6624c9&' +
                  'v=5.131')
                .then(response=>this.idLocation=response.data.response.items)
          },
            onInputUniversities() {
                axios.get('https://api.vk.com/method/database.getUniversities?' +
                    'country_id=1&' +
                    'city_id='+ this.idLocation[0].id+
                    '&count=10&' +
                    'access_token=16bd660e592e5759f2a2cdccd3562b4c8613fb4d03cb49ed0012b38f57f4878a9108d6d50d6bc7c6624c9&' +
                    'v=5.131')
                    .then(response=>this.info.VkUniversities=response.data.response.items)
            },
        },
        computed: {
            ButtonMessage: function () {
                switch (this.info.VisibleResume) {
                    case true: return 'Скрыть резюме'
                    case false: return 'Показать резюме'
                }
            },
            isPhoneError() {
                if(this.info.isPhoneTouched){
                    return this.info.PhoneNumber.length < 6 ||
                        this.info.PhoneNumber.length >10 ||
                        isNaN(this.info.PhoneNumber);
                }
            },
        },
        mounted() {
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

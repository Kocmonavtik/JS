<template>
  <div class="w-full max-w-2xl">
    <p>{{VK}}</p>
    <p class="text-4xl pb-4">Ваше резюме</p>

    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">

      <div class="grid grid-rows-1 grid-cols-5 gap-4 pb-1">
        <div class="col-span-2">
          <p class="flex items-center text-lg">Ссылка на фото</p>
          <textarea class="form-textarea shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                    v-model="Image"></textarea>
        </div>
        <div class="row-span-1 col-span-3">
          <div class="flex flex-wrap justify-center">
            <div class="w-full sm:w-6/12 px-4">
              <img
                src= ""
                alt="..."
                class="shadow-xl rounded-full max-w-full h-auto align-middle border-none"
                v-bind:src="ImageSrc">
            </div>
          </div>
        </div>
      </div>

      <p class="text-2xl flex flex-row pb-4">Контактные данные</p>
      <div class="grid grid-cols-3 gap-4 pb-3">
        <p class="flex items-center text-lg">Имя</p>
        <div class="col-span-2">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model="FirstName">
        </div>
      </div>

      <div class="grid grid-cols-3 gap-4 pb-8">
        <p class="flex items-center text-lg">Фамилия</p>
        <div class="col-span-2">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model="SecondName">
        </div>
      </div>

      <div class="grid grid-cols-3 gap-4 pb-3">
        <p class="flex items-center text-lg">Мобильный телефон</p>
        <div class="col-span-2">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model="PhoneNumber"  @blur="isPhoneTouched = true" v-bind:placeholder='89990888552'>
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
                 v-model="Email">
        </div>
      </div>

      <div class="grid grid-cols-3 gap-4 pb-8">
        <p class="flex items-center text-lg">Город проживания</p>
        <div class="col-span-2">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model="LocationUser">
        </div>
      </div>

      <p class="text-2xl flex flex-row pb-4">Основная информация</p>
      <div class="grid grid-cols-3 gap-4 pb-3">
        <p class="flex items-center text-lg">Дата рождения</p>
        <div class="col-span-2">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 type="date" v-model="Birthday">
        </div>
      </div>

      <div class="grid grid-cols-3 gap-4 pb-3">
        <p class="flex items-center text-lg">Желаемая зарплата</p>
        <div class="col-span-2 grid grid-cols-5 gap-4">
          <div class="col-span-4 ">
            <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                   v-model="Salary" >
          </div>
          <div class="relative inline-block w-full text-gray-700">
            <select class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                    v-model="Currency">
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

      <div class="grid grid-cols-3 gap-4 pb-3">
        <p class="flex items-center text-lg">Образование</p>
        <div class="col-span-2">
          <div class="relative inline-block w-full text-gray-700">
            <select class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                    v-model="Education">
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
        <div v-if="Education !='Среднее'">
          <div class="grid grid-cols-3 gap-4 pt-3 pb-3">
            <p class="flex items-center text-lg">Учебное заведение</p>
            <div class="col-span-2">
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                     v-model="EduInstitution">
            </div>
          </div>

          <div class="grid grid-cols-3 gap-4 pb-3">
            <p class="flex items-center text-lg">Факультет</p>
            <div class="col-span-2">
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                     v-model="Faculty">
            </div>
          </div>

          <div class="grid grid-cols-3 gap-4 pb-3">
            <p class="flex items-center text-lg">Специализация</p>
            <div class="col-span-2">
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                     v-model="Specialization">
            </div>
          </div>

          <div class="grid grid-cols-3 gap-4 pb-6">
            <p class="flex items-center text-lg">Год окончания</p>
            <div class="col-span-2">
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                     v-model="YearEnd">
            </div>
          </div>
        </div>
      </transition>

      <div class="grid grid-cols-3 gap-4 pb-8">
        <p class="flex items-center text-lg">Ключевые навыки</p>
        <div class="col-span-2">
          <textarea class="form-textarea shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                    v-model="KeySkills">
          </textarea>

        </div>
      </div>

      <div class="grid grid-cols-3 gap-4 pb-8">
        <p class="flex items-center text-lg">О себе</p>
        <div class="col-span-2">
          <textarea class="form-textarea shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                    v-model="AboutMe">

          </textarea>
        </div>
      </div>

      <div class="">
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                type="button" v-on:click="VisibleResume = !VisibleResume">
          {{ButtonMessage}}
        </button>
      </div>
    </form>


    <transition name="fade">
      <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" v-if="VisibleResume">

        <div class="grid grid-rows-1 grid-cols-5 gap-4 pb-8">
          <div class="col-span-2">
            <p class="flex items-center text-3xl">{{FirstName}} {{SecondName}}</p>
            <p class="flex items-center text-sm pb-4">{{Years}} {{Word}}, родился {{Birthday}}</p>
            <p class="flex items-center text-lg">Контакты</p>
            <p class="flex items-center text-sm ">+7{{PhoneNumber}}</p>
            <p class="flex items-center text-sm pb-4">{{Email}}</p>
            <p class="flex items-center text-lg">Место проживания: {{LocationUser}}</p>
          </div>
          <div class="row-span-1 col-span-3">
            <div class="flex flex-wrap justify-center">
              <div class="w-full sm:w-6/12 px-4">
                <img
                  src= ""
                  alt="..."
                  class="shadow-xl rounded-full max-w-full h-auto align-middle border-none" v-bind:src="ImageSrc"/>
              </div>
            </div>
          </div>
        </div>

        <div class="grid grid-rows-1 grid-cols-5 gap-4 pb-4">
          <div class="col-span-3">
            <p class="text-left text-2xl pb-4">{{Education}} образование</p>
            <div v-if="Education !='Среднее'">
              <p class="text-left text-lg">Учебное заведение: {{EduInstitution}}</p>
              <p class="text-left text-sm">{{Faculty}}</p>
              <p class="text-left text-sm ">Специализация: {{Specialization}}</p>
              <p class="text-left text-sm pb-4">Год окончения: {{YearEnd}}</p>
            </div>
            <p class="text-left text-lg">Ключевые навыки</p>
            <p class="text-left text-sm pb-4">{{KeySkills}}</p>
            <p class="text-left text-lg">О себе</p>
            <p class="text-left text-sm">{{KeySkills}}</p>
          </div>
          <div class="row-span-1 col-span-2">
            <p class="text-right text-2xl "> Желаемая зарплата</p>
            <p class="text-right text-2xl " >{{Salary}} {{Currency}}</p>
          </div>
        </div>

      </form>
    </transition>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data () {
      return {
        errors: [],
        Image:'',
        Education: 'Среднее',
        Currency: '',
        PhoneNumber : '',
        isPhoneTouched: false,
        FirstName: '',
        SecondName: '',
        Birthday:  '',
        Email: '',
        LocationUser: '',
        Salary: '',
        EduInstitution: '',
        Faculty: '',
        Specialization: '',
        YearEnd: '',
        KeySkills: '',
        AboutMe: '',
        VisibleResume: false,
        VK: null
      }
    },
    /*watch: {
      PhoneNumber: 'CheckNumber',
    },
    methods: {
      CheckNumber() {
        const {PhoneNumber,errors}=this;

        if(Number.isNaN(PhoneNumber)){
          errors.PhoneNumber='Введите корректный номер телефона'
        }
        else {
          errors.PhoneNumber=''
        }
      }
    },*/
    watch: {
      Education: 'CheckEducation',//создание функции по просмотру артрибута Education
    },
    methods: {
      CheckEducation() {//Функция проверки и создание алгоритма
        if(this.Education == 'Среднее')
          this.Faculty=''
        this.EduInstitution=''
        this.Specialization=''
        this.YearEnd=''
      }
    },
    computed: {
      ImageSrc: {
        get: function () {
          return this.Image;
        }
      },
      Years: {
        get:function () {
          let now= new Date();
          let old=new Date(this.Birthday.replace('/(\d{4})\.(\d{2})\.(\d{2})/)','$1-$2-$3'));
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
      isPhoneError() {
        if(this.isPhoneTouched){
          return this.PhoneNumber.length < 6 ||
            this.PhoneNumber.length >11 ||
            isNaN(this.PhoneNumber);
        }
      },
      ButtonMessage: function () {
        switch (this.VisibleResume) {
          case true: return 'Скрыть резюме'
          case false: return 'Показать резюме'
        }
      },
      mounted() {
        axios.get("https://api.vk.com/method/users.get?user_ids=132555922&fields=bdate&access_token=16bd660e592e5759f2a2cdccd3562b4c8613fb4d03cb49ed0012b38f57f4878a9108d6d50d6bc7c6624c9&v=5.131")
          .then(response => this.VK= response.data());
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .4s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
    opacity: 0;
  }
</style>

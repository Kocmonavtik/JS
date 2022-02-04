<template>
  <div class="w-full max-w-2xl">
    <p class="text-4xl">Ваше резюме</p>
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <p class="text-2xl flex flex-row pb-4">Контактные данные</p>
      <div class="flex flex-wrap pb-3">
        <div class="grid">
          <p class="place-self-center flex flex-row pr-32 text-lg">Имя</p>
        </div>
        <div class="flex-1">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" v-model.number="feet" v-bind:placeholder="feet_value">
        </div>
      </div>
      <div class="flex flex-wrap pb-3">
        <div class="grid">
          <p class="place-self-center flex flex-row pr-32 text-lg">Фамилия</p>
        </div>
        <div class="flex-1">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" v-model.number="feet" v-bind:placeholder="feet_value">
        </div>
      </div>


      <p class="text-2xl flex flex-row pb-4">Контактные данные</p>
      <div class="grid grid-cols-3 gap-4 pb-3">
        <p class="flex items-center text-lg">Имя</p>
        <div class="col-span-2">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" v-model.number="feet" v-bind:placeholder="feet_value">
        </div>
      </div>
      <div class="grid grid-cols-3 gap-4 pb-3">
        <p class="flex items-center text-lg">Фамилия</p>
        <div class="col-span-2">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" v-model.number="feet" v-bind:placeholder="feet_value">
        </div>
      </div>
    </form>
  </div>
</template>

<script>
    export default {
        name: "test"
    }
</script>

<style scoped>

</style>
<form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" @submit.prevent="someAction2()">
  <div class="grid grid-cols-5 pb-1">
    <div class="col-span-3">
      <div class="grid grid-rows-3 gap-2 pb-1">
        <div class="row-span-1 col-span-2">
          <p class="flex items-center text-lg">{{FirstName}} {{SecondName}}</p>
          <p class="flex items-center text-lg">,родился {{Birthday}}</p>
        </div>

        <div class="row-span-1 col-span-2">
          <p class="flex items-center text-lg">Контакты</p>
          <p class="flex items-center text-lg">+7{{PhoneNumber}}</p>
          <p class="flex items-center text-lg">{{Email}}</p>
        </div>

        <div class="row-span-1 col-span-2">
          <p class="flex items-center text-lg">Место проживания: {{LocationUser}}</p>
        </div>
      </div>
    </div>
    <div class="col-span-2">
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

</form>

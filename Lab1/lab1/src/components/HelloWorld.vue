<template>
  <div class="w-full max-w-3xl">
    <p class="text-4xl">Конвертация величин</p>
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <div class=" flex flex-nowrap mb-4 space-x-4">
        <div class="flex flex-col w-full">
          <p>Футы</p>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model.number="feet" v-bind:placeholder="feet_value">
        </div>
        <div class="flex flex-col w-full">
          <p>Метры</p>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model.number="metres" v-bind:placeholder="metres_value">
        </div>
      </div>
      <div class="flex flex-nowrap mb-4 space-x-4">
        <div class="flex flex-col w-full">
          <p>Морские мили</p>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model.number="nm" v-bind:placeholder="nm_value">
        </div>
        <div class="flex flex-col w-full">
          <p>Километры</p>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model.number="kilometres" v-bind:placeholder="kilometres_value">
        </div>
      </div>
      <div class=" flex flex-nowrap mb-4 space-x-4">
        <div class="flex flex-col w-full">
          <p>Градусы</p>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model.number="degrees" v-bind:placeholder="degrees_value">
        </div>
        <div class="flex flex-col w-full">
          <p>Радианы</p>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model.number="radians" v-bind:placeholder="radians_value">
        </div>
      </div>
      <div class=" flex flex-nowrap mb-4 space-x-4">
        <div class="flex flex-col w-full">
          <p>Градусы по Фаренгейту</p>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model.number="fahrenheit" v-bind:placeholder="fahrenheit_value">
        </div>
        <div class="flex flex-col w-full">
          <p>Градусы по Цельсию</p>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                 v-model.number="celsium" v-bind:placeholder="celsium_value">
        </div>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'test1',
    data () {
      return {
        feet: '',
        metres: '',
        nm: '',
        kilometres: '',
        degrees: '',
        radians: '',
        fahrenheit: '',
        celsium: ''
      }
    },
    computed: {
      feet_value: {
        get: function () {
          return this.metres * 3.28084
        }
      },
      metres_value: {
        get: function () {
          return this.feet / 3.28084
        }
      },
      nm_value: {
        get: function () {
          return this.kilometres / 1.852
        }
      },
      kilometres_value: {
        get: function () {
          return this.nm * 1.852
        }
      },
      degrees_value: {
        get: function () {
          return this.radians * (180 / Math.PI)
        }
      },
      radians_value: {
        get: function () {
          return this.degrees * (Math.PI / 180)
        }
      },
      fahrenheit_value: {
        get: function () {
          return (this.celsium * (9 / 5) + 32)
        }
      },
      celsium_value: {
        get: function () {
          return ((this.fahrenheit - 32) * (5 / 9))
        }
      }
    }
  }
</script>


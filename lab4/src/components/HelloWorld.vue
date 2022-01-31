<template>
  <div class="w-full max-w-2xl">
    <InputForm :info="info"></InputForm>
    <OutputForm :info="info"></OutputForm>
  </div>
</template>

<script>
  import InputForm from "./InputForm.vue";
  import OutputForm from "./OutputForm.vue";
  import axios from 'axios'
  export default {
    name: 'HelloWorld',
    components: {OutputForm, InputForm},
    data () {
      return {
        info: {
          errors: [],
          Image: undefined,
          Education: [{classEdu: 'Среднее', EduInstitution:'', Faculty: '',Specialization: '', YearEnd: ''}],
          Currency: '',
          PhoneNumber: '',
          isPhoneTouched: false,
          FirstName: '',
          SecondName: '',
          Birthday: '',
          Email: '',
          LocationUser: '',
          Salary: '',
          KeySkills: '',
          AboutMe: '',
          VisibleResume: false,
          VkCity: '{ "id":, "title":, "important": 1 }',
          VkUniversities: '{"id":,"title":,"important":1}',
          Status: 'New'
        }
      }
    },
  }
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<!--<style scoped>
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
</style>-->

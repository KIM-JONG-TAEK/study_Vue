<template>
  <section class="container">
    <!-- <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3> -->
    <user-data class="test" :first-name="firstName" :last-name="lastName"></user-data>
    <button @click="setAge">Change Age</button>
    <div>
      <!-- <input type="text" placeholder="First Name" @input="setFirstName" />
      <input type="text" placeholder="Last Name" @input="setLastName" /> -->
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <button @click="setLastName">Set Last Name</button>
    </div>
  </section>
</template>

<script>
// import { ref } from 'vue';
// import { reactive } from 'vue';
// import { reactive, toRefs } from 'vue';
import { ref, computed, watch, provide } from 'vue';
import UserData from './components/UserData.vue';

export default {
  components: {
    UserData
  },
  setup() {
    // const uName = ref('Kerwin');
    const firstName = ref('');
    const lastName = ref('');
    const lastNameInput = ref(null);
    const uAge = ref(29);

    // const user = ref({
    //   name: 'Kerwin',
    //   age: 29
    // });

    // const user = reactive({
    //   name: 'Kerwin',
    //   age: 29
    // });

      provide('userAge', uAge);

    const uName = computed(function () {
      return firstName.value + ' ' + lastName.value;
    });

    watch([uAge, uName], function (newValues, oldValues) {
      console.log('Old age: ' + oldValues[0]);
      console.log('New age: ' + newValues[0]);
      console.log('Old name: ' + oldValues[1]);
      console.log('New name: ' + newValues[1]);
    });

    function setNewAge() {
      uAge.value = 30;
    }

    function setLastName() {
      lastName.value = lastNameInput.value.value;
    }

    // function setFirstName(event) {
    //   firstName.value = event.target.value;
    // }

    // function setLastName(event) {
    //   lastName.value = event.target.value;
    // }

    // setTimeout(function () {
    //   // uName.value = 'Kim';
    //   // uAge.value = 30;

    //   // user.value.name = 'Kim';
    //   // user.value.age = 30;

    //   user.name = 'Kim';
    //   user.age = 30;
    // }, 2000);

    // const userRefs = toRefs(user);

    return { userName: uName, age: uAge, setAge: setNewAge, firstName, lastName, lastNameInput, setLastName };
    // return { user: user, userName: userRefs.name, age: userRefs.age };
    // return { user: user, setAge: setNewAge };
  },
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //     age: 29
  //   };
  // },
  // methods: {
  //   setNewAge() {
  //     this.age = 30;
  //   }
  // },
  // watch: {
  //   age(val) {
  //     console.log(val);
  //   }
  // },
  // provide() {
  //   return { age: this.age };
  // }
};
</script>

<!-- <script setup>
import { ref } from 'vue';
 
const uName = ref('Maximilian');
 
setTimeout(function() {
  uName.value = 'Max';
}, 2000);
</script> -->

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
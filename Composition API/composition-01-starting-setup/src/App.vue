<template>
  <section class="container">
    <!-- <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3> -->
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
  </section>
</template>

<script>
// import { ref } from 'vue';
// import { reactive } from 'vue';
// import { reactive, toRefs } from 'vue';
import { reactive } from 'vue';

export default {
  setup() {
    // const uName = ref('Maximilian');
    // const uAge = ref(29);
    
    // const user = ref({
    //   name: 'Kerwin',
    //   age: 29
    // });

    const user = reactive({
      name: 'Kerwin',
      age: 29
    });

    setTimeout(function () {
      // uName.value = 'Kim';
      // uAge.value = 30;
      
      // user.value.name = 'Kim';
      // user.value.age = 30;

      user.name = 'Kim';
      user.age = 30;
    }, 2000);

    // const userRefs = toRefs(user);

    // return { userName: uName, age: uAge };
    // return { user: user, userName: userRefs.name, age: userRefs.age };
    return { user: user };
  }
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
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
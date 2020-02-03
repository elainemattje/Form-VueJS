<template>
  <div id="app">
    <!-- <NewUserForm></NewUserForm> -->
    <!-- <NewUserForm /> -->
    <!-- <MyPlayground :msg="appName"></MyPlayground> -->
    <UserForm></UserForm>
  </div>
</template>

<script>
// import NewUserForm from "./components/NewUserForm.vue";
// import NewUserForm from "./components/NewUserForm.vue";
// import MyPlayground from "./components/MyPlayground.vue";
import UserForm from "./components/UserForm.vue";

export default {
  name: "app",
  components: {
    // NewUserForm
    // MyPlayground
    UserForm
  }
  // data() {
  //   return {
  //     appName: "MyApp"
  //   };
  // }
};
</script>



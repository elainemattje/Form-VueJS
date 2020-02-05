<template>
  <div id="app">
    <!-- <NewUserForm></NewUserForm> -->
    <!-- <NewUserForm /> -->
    <!-- <MyPlayground :msg="appName"></MyPlayground> -->
    <UserForm></UserForm>
    <!-- <Axios_API></Axios_API> -->
  </div>
</template>

<script>
// import NewUserForm from "./components/NewUserForm.vue";
// import NewUserForm from "./components/NewUserForm.vue";
// import MyPlayground from "./components/MyPlayground.vue";
import UserForm from "./components/UserForm.vue";
// import Axios_API from "./components/Axios_API.vue";

export default {
  name: "app",
  components: {
    // NewUserForm
    // MyPlayground
    UserForm
    // Axios_API
  }
  // data() {
  //   return {
  //     appName: "MyApp"
  //   };
  // }
};
</script>



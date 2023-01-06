<script>
import Butter from "buttercms";

export default {
  name: "HomePage",

  data() {
    return {
      image: null,
      title: null,
      description: null,
    };
  },

  mounted() {
    const butter = Butter(import.meta.env.VITE_BUTTER_API_KEY);

    butter.page
      .retrieve("*", "home")
      .then((resp) => {
        ({
          image: this.image,
          title: this.title,
          description: this.description,
        } = resp.data.data.fields.header_component);
      })
      .catch(function (resp) {
        console.log(resp);
      });
  },
};
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>

<script setup>
import Formik from "./components/Formik.vue";

const submit = (data) => {
  console.log("debug here", data);
};
</script>

<template>
  <main>
    <Formik @submitFinal="submit" :validate="() => {}" v-slot="{ handleSubmit }"
      ><form @submit.prevent="handleSubmit">
        <button type="submit">sdgdsreg</button>
      </form>
    </Formik>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

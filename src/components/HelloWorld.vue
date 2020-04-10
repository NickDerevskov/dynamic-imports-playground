<template>
  <main>
    Some text

    <button @click="changeColorScheme('first')">First module</button>
    <button @click="changeColorScheme('second')">Second module</button>
  </main>
</template>

<script>
/* Static import just for see difference */
// import '../imports/one.scss';
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      colorScheme: "something"
    };
  },
  methods: {
    async changeColorScheme(data) {
      this.colorScheme = data;
      console.log(this.colorScheme);
      if (this.colorScheme === "first") {
        await import(
          /* webpackChunkName: "ONE_SCSS_CHUNK" */ "../imports/one.scss"
        );
      } else if (this.colorScheme === "second") {
        await import(
          /* webpackChunkName: "TWO_SCSS_CHUNK" */ "../imports/two.scss"
        );
      }
    }
  }
};
</script>

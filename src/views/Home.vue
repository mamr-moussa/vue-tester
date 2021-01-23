<template>
  <div>
    the count is {{ count }}
    <button @click="increment">Incement</button>
    the sum is {{ sum }}
    <button @click="incrementSum">Incement</button>
    <p>Total is: {{ total }}</p>

    <my-input
      v-for="(field, index) in form"
      :key="index"
      :placeholder="field.placeholder"
      :input-type="field.inputType"
      show-label
    />
  </div>
</template>

<script>
import MyInput from "@/components/MyInput";
export default {
  // name
  name: "HomeComponent",
  components: {
    MyInput
  },
  // data
  data() {
    return {
      count: 0,
      sum: 0,
      form: null
    };
  },
  // computed
  computed: {
    total() {
      return this.count + this.sum;
    }
  },
  // watch
  watch: {
    total(val) {
      if (val % 2 === 0) {
        // alert("zawgy " + val);
      }
    },
    sum(val, before) {
      console.log("sum is now " + val + "it was " + before);
    }
  },
  // methods
  methods: {
    increment() {
      this.count += 1;
    },
    incrementSum() {
      this.sum += 1;
    },
    getForm() {
      this.form = [
        { placeholder: "username", inputType: "text" },
        { placeholder: "first name", inputType: "text" },
        { placeholder: "last name", inputType: "text" },
        { placeholder: "password", inputType: "password" }
      ];
    }
  },

  // beforeCreated
  // created
  // beforeMounted
  // mounted
  mounted() {
    this.getForm();
  }
  // beforeDestoried
  // destroied
};
</script>

<style lang="css" scoped></style>

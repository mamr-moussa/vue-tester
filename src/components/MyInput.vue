<template>
  <div>
    <label v-if="showLabel">{{ placeholder }}</label>
    <input
      v-model="val"
      :placeholder="placeholder"
      :type="inputType"
      :class="[
        'input',
        { valid: isValid && isValid.valid },
        { invalid: isValid && !isValid.valid }
      ]"
    />
    <p v-if="isValid && !isValid.valid">{{ isValid.error }}</p>
  </div>
</template>

<script>
export default {
  name: "MyInput",
  props: {
    placeholder: {
      type: String,
      default: "Enter a text.."
    },
    inputType: {
      type: String,
      default: "text"
    },
    showLabel: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      val: ""
    };
  },
  computed: {
    isValid() {
      return this.validate(this.val);
    }
  },
  methods: {
    validate(input) {
      let result = { valid: true, error: null };
      if (!input || !input.length) {
        result.valid = false;
        result.error = "text cannot be empty";
      }

      return result;
    }
  }
};
</script>

<style lang="css" scoped>
.valid {
  color: green;
  border: 1px solid green;
}
.invalid {
  color: red;
  border: 1px solid red;
}
</style>

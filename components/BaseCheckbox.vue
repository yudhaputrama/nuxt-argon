<template>
  <div class="custom-control custom-checkbox"
       :class="[{disabled: disabled}, inlineClass]">
    <input :id="cbId"
           class="custom-control-input"
           type="checkbox"
           :disabled="disabled"
           v-model="model"/>
    <label :for="cbId" class="custom-control-label">
      <slot>
        <span v-if="inline">&nbsp;</span>
      </slot>
    </label>
  </div>
</template>
<script>
// import { randomString } from "./stringUtils";

function randomString(length = 7) {
  const possibleChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
  let text = "";

  for (let i = 0; i < length; i++)
    text += possibleChars.charAt(Math.floor(Math.random() * possibleChars.length));

  return text;
}


export default {
  name: "base-checkbox",
  model: {
    prop: "checked"
  },
  props: {
    checked: {
      type: [Array, Boolean],
      description: "Whether checkbox is checked"
    },
    disabled: {
      type: Boolean,
      description: "Whether checkbox is disabled"
    },
    inline: {
      type: Boolean,
      description: "Whether checkbox is inline"
    }
  },
  data() {
    return {
      cbId: "",
      touched: false
    };
  },
  computed: {
    model: {
      get() {
        return this.checked;
      },
      set(check) {
        if (!this.touched) {
          this.touched = true;
        }
        this.$emit("input", check);
      }
    },
    inlineClass() {
      if (this.inline) {
        return `form-check-inline`;
      }
    }
  },
  mounted() {
    this.cbId = randomString()
  }
};
</script>

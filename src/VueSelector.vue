<template>
  <div :class="layout">
    <label
      class="input-selector"
      v-for="option in options"
      :key="option[keyField]"
      :for="option[keyField]"
      :class="getSelectedClass(option)"
    >
      <input
        :type="type"
        :id="option[keyField]"
        :value="valueField ? option[valueField] : option"
        v-model="model"
        v-show="show"
        :disabled="!!option.disabled"
        @focus="onFocus"
        @blur="onBlur"
        @change="onChange"
      />
      <slot :option="option">{{ option[labelField] }}</slot>
    </label>
  </div>
</template>

<script>
export default {
  name: "Selector",
  props: {
    value: {},
    options: {
      type: Array,
      default() {
        return [];
      },
    },
    multiple: {
      type: Boolean,
      default: false,
    },
    show: {
      type: Boolean,
      default: false,
    },
    layout: {
      type: String,
      default: "vertical",
    },
    activeClass: {
      type: String,
      default: "selected-item",
    },
    disabledClass: {
      type: String,
      default: "disabled-item",
    },
    limit: {
      type: Number,
      default: 0,
    },
    keyField: {
      type: String,
      default: "id",
    },
    valueField: {
      type: String,
      default: null,
    },
    labelField: {
      type: String,
      default: "label"
    }
  },
  methods: {
    onChange() {
      this.$nextTick(() => {
        this.$emit("change", this.model);
      });
    },
    onFocus() {
      this.$emit("focus");
    },
    onBlur() {
      this.$emit("blur");
    },
    getSelectedClass(option) {
      const matchVal = this.valueField ? option[this.valueField] : option;
      if (this.multiple) {
        return this.model.includes(matchVal) ? this.activeClass : option.disabled ? this.disabledClass : "";
      } 
      else {
        return this.model === matchVal ? this.activeClass : option.disabled ? this.disabledClass : "";
      }
    },
    clearAll() {
      this.model = {};
    }
  },
  computed: {
    selectedValue() {
      let value = this.value;
      if (value) {
        return [].concat(value);
      }
      return [];
    },
    type() {
      return this.multiple ? "checkbox" : "radio";
    },
    model: {
      get() {
        return this.value;
      },
      set(val) {
        const len = Array.isArray(val) ? val.length : 1;
        if (this.value !== val && (this.limit === 0 || len <= this.limit)) {
          this.$emit("input", val);
        }
      },
    },
  },
};
</script>
<style>
.input-selector {
  cursor: pointer;
  margin: 10px;
  display: flex;
  align-items: center;
}
</style>
<style scoped>
.vertical {
  display: flex;
  flex-direction: column;
}
.horizontal {
  display: flex;
  flex-direction: row;
}
input[type="checkbox"],
input[type="radio"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  padding: 0;
  height: 20px;
  width: 20px;
  margin: 3px 5px 3px 5px;
}
.disabled-item {
  opacity: 0.5;
  cursor: not-allowed;
}
.selected-item {
  border: 2px solid red;
}
</style>

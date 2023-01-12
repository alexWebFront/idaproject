<template>
  <select
      :value="modelValue"
      @change="changeOption">
    <option disabled value="">По умолчанию</option>
    <option
        v-for="option in options"
        :key="option.value"
        :value="option.value">{{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: "my-select",

  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>
select{
  font-family: 'Source Sans Pro', sans-serif;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  padding: 10px 15px;
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  color: #B4B4B4;
  outline: none;
  /*appearance: none;*/
  /*background: url("@/assets/icons/arrow.svg") no-repeat right;*/
  /*background-position-x: calc(100% - 8px);*/
  min-width: 122px;
  background-color: #FFFEFB;
}

</style>


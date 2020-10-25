<template>
  <div class="group-or-rule-container rule-container">
    <div class="rule group-or-rule">
      <div class="rule--body--wrapper">
        <div class="rule--body flex">
          <div class="rule--field">
            <q-input
              v-if="editMode"
              dense
              type="text"
              :rules="[val => !!val || 'Field is required']"
              hint=" "
              label="Field"
              v-model="value.field"
            />
            <label v-else>{{ value.field }}</label>
          </div>
          <div class="rule--operator">
            <q-input
              v-if="editMode"
              dense
              type="text"
              :rules="[val => !!val || 'Operator is required']"
              hint=" "
              label="Operator"
              v-model="value.operator"
            />
            <label v-else>{{ value.operator }}</label>
          </div>
          <div class="rule--value">
            <q-input
              v-if="editMode"
              dense
              type="text"
              :rules="[val => !!val || 'Value is required']"
              hint=" "
              label="Value"
              v-model="value.value"
            />
            <label v-else>{{ value.value }}</label>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RuleContainer",
  props: {
    value: {
      type: Object,
      default: () => ({ field: "", operator: "", value: "" }),
    },
    editMode: {
      type: Boolean,
      default: () => true,
    },
  },
  data() {
    return {};
  },
};
</script>

<style scoped></style>

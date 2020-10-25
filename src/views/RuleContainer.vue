<template>
  <div class="group-or-rule-container rule-container">
    <div class="rule group-or-rule">
      <div class="rule--body--wrapper">
        <div class="rule--body flex">
          <div class="rule--field">
            <q-input
              dense
              type="text"
              :rules="[val => !!val || 'Field is required']"
              hint=" "
              label="Field"
              v-model="field"
            />
          </div>
          <div class="rule--operator">
            <q-input
              dense
              type="text"
              :rules="[val => !!val || 'Operator is required']"
              hint=" "
              label="Operator"
              v-model="operator"
            />
          </div>
          <div class="rule--value">
            <q-input
              dense
              type="text"
              :rules="[val => !!val || 'Value is required']"
              hint=" "
              label="Value"
              v-model="value"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RuleContainer",
  data() {
    return {
      field: "",
      operator: "",
      value: "",
    };
  },
};
</script>

<style scoped></style>

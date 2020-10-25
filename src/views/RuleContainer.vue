<template>
  <div class="group-or-rule-container rule-container">
    <div class="rule group-or-rule">
      <div class="rule--body--wrapper">
        <div class="rule--body flex row">
          <div
            class="rule--field col content-end"
            style="justify-content: start;"
          >
            <q-input
              outlined
              v-if="editMode"
              dense
              style="width: 95%"
              type="text"
              :rules="[val => !!val || 'Field is required']"
              hint=" "
              label="Field"
              v-model="value.field"
            />
            <label v-else>{{ value.field }}</label>
          </div>
          <div class="rule--operator col-3">
            <q-select
              v-if="editMode"
              style="width: 95%"
              dense
              outlined
              v-model="value.operator"
              :options="options"
              :rules="[val => !!val || 'Operator is required']"
              hint=" "
              label="Operator"
            />
            <!--<q-input
                v-if="editMode"
                dense
                style="width: 95%"
                type="text"
                :rules="[val => !!val || 'Operator is required']"
                hint=" "
                label="Operator"
                v-model="value.operator"
            />-->
            <label v-else>{{ value.operator }}</label>
          </div>
          <div class="rule--value col-5">
            <q-input
              outlined
              v-if="editMode && value.operator === '='"
              dense
              style="width: 95%"
              type="text"
              :rules="[val => !!val || 'Value is required']"
              hint=" "
              label="Value"
              v-model="value.value"
            />
            <q-input
              outlined
              v-else-if="editMode && value.operator === 'includes'"
              dense
              style="width: 95%"
              type="textarea"
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
    return {
      model: null,
      options: ["=", "includes"],
    };
  },
};
</script>

<style scoped></style>

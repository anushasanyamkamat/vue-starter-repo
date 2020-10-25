<template>
  <div class="group-or-rule-container group-container">
    <div class="group group-or-rule">
      <div class="group--header flex">
        <div class="group--conjunctions block flex-1" style="flex: 1">
          <div class="">
            <q-btn-toggle
              v-if="editMode"
              v-model="value.concat"
              toggle-color="primary"
              :options="[
                { label: 'AND', value: 'AND' },
                { label: 'OR', value: 'OR' },
              ]"
            />
            <q-btn
              class="bg-primary text-white"
              v-else
              disable
              v-model="value.concat"
              toggle-color="primary"
              :label="value.concat"
            />
          </div>
        </div>
        <div
          v-if="editMode"
          class="group--actions group--actions--tr flex justify-end content-end"
        >
          <div class="">
            <q-btn
              size=""
              class="q-mr-sm"
              @click="onClick"
              color="primary"
              type="button"
            >
              Add rule
            </q-btn>
            <q-btn @click="onGroupClick" color="primary" type="button">
              Add group
            </q-btn>
          </div>
        </div>
      </div>
      <div class="group--children hide--line one--child" ref="container">
        <template v-for="(item, idx) in value.children">
          <component
            :edit-mode="editMode"
            :is="item.type"
            :key="idx"
            v-model="value.children[idx]"
          ></component>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
import RuleContainer from "@/views/RuleContainer";
import GroupContainer from "@/views/GroupContainer";

export default {
  name: "GroupContainer",
  data() {
    return {
      defaultConcat: "AND",
      children: [],
    };
  },
  components: {
    RuleContainer: RuleContainer,
    GroupContainer: GroupContainer,
  },
  props: {
    value: {
      type: Object,
      default: () => ({ concat: "AND", children: [] }),
    },
    editMode: {
      type: Boolean,
      default: () => true,
    },
  },
  mounted() {
    console.log(this.editMode);
    console.log(this.value);
  },
  methods: {
    onClick() {
      this.value.children.push({
        type: "RuleContainer",
        field: "",
        operator: "",
        value: "",
      });
    },
    onGroupClick() {
      this.value.children.push({
        type: "GroupContainer",
        concat: "AND",
        children: [],
      });
    },
  },
};
</script>

<style lang="scss">
.group--children
  > .group-or-rule-container:first-child
  > .group-or-rule::before {
  top: -12px;
  height: calc(50% + 14px);
}

.group--children > .group-or-rule-container > .group-or-rule::before,
.group--children > .group-or-rule-container > .group-or-rule::after {
  content: "";
  position: absolute;
  left: -14px;
  width: 14px;
  height: calc(50% + 8px);
  border-color: #ccc;
  border-style: solid;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.group--children > .group-or-rule-container > .group-or-rule:before {
  top: -4px;
  border-width: 0 0 2px 2px;
}

.group--children > .group-or-rule-container > .group-or-rule::after {
  top: 50%;
  border-width: 0 0 0 2px;
}

.group-or-rule-container:last-child {
  margin-bottom: 0px !important;
}

.group-or-rule-container:first-child {
  margin-top: 0px !important;
}

.group-or-rule-container {
  margin-top: 10px;
  margin-bottom: 10px;
  padding-right: 10px;
}

.query-builder *,
.query-builder *::before,
.query-builder *::after {
  box-sizing: border-box;
}

div {
  display: block;
}

.group-or-rule {
  border-radius: 5px;
  position: relative;
}

.group--header,
.group--footer {
  padding-left: 10px;
  padding-right: 5px;
  margin-top: 10px;
  margin-bottom: 10px;
}

.group--children {
  margin-top: 10px;
  margin-bottom: 10px;
}

.group--children {
  padding-left: 24px;
}

.group {
  background: white;
  border: 1px solid #cdcdcd;
}

.query-builder *,
.query-builder *::before,
.query-builder *::after {
  box-sizing: border-box;
}

.group-or-rule-container:last-child {
  margin-bottom: 0px !important;
}

.group-or-rule-container:first-child {
  margin-top: 0px !important;
}

.group-or-rule-container {
  margin-top: 10px;
  margin-bottom: 10px;
  padding-right: 10px;
}

.rule {
  flex: 1;
  display: flex;
}

.group-or-rule {
  border-radius: 5px;
  position: relative;
}

.rule {
  background-color: #e8f0fe;
  border: 1px solid transparent;
  padding: 10px;
}

.rule--body--wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
}

.rule--field,
.group--field,
.rule--operator,
.rule--value,
.rule--operator-options,
.rule--widget,
.widget--widget,
.widget--valuesrc,
.widget--sep,
.operator--options--sep,
.rule--before-widget,
.rule--after-widget {
  display: flex;
  flex: 1;
}

.group--children.hide--conjs
  > .group-or-rule-container:first-child
  > .group-or-rule::before {
  display: none;
}

.group--children.hide--conjs
  > .group-or-rule-container:first-child
  > .group-or-rule::after {
  border-radius: 4px 0 0 0;
  border-width: 2px 0 0 2px;
}

.group--children.rule_group--children
  > .group-or-rule-container:first-child
  > .group-or-rule::before {
  display: none;
}

.group--children.rule_group--children
  > .group-or-rule-container:first-child
  > .group-or-rule::after {
  border-radius: 4px 0 0 0;
  border-width: 2px 0 0 2px;
}

.group--children
  > .group-or-rule-container:first-child
  > .group-or-rule::before {
  top: -12px;
  height: calc(50% + 14px);
}

.group--children
  > .group-or-rule-container:last-child
  > .group-or-rule::before {
  border-radius: 0 0 0 4px;
}

.group--children > .group-or-rule-container:last-child > .group-or-rule::after {
  display: none;
}
</style>

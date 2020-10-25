<template>
  <div
    class="audience-builder query-builder-container"
    style="width: 900px; margin: 0 auto;padding: 30px"
  >
    <div class="query-builder qb-lite">
      <div class="text-h5 q-mt-md">EDIT MODE</div>
      <GroupContainer edit-mode v-model="initialQuery" />

      <div class="text-h5 q-mt-md">VIEW</div>
      <GroupContainer :edit-mode="false" v-model="initialQuery" />
    </div>
    <div class="text-h5 q-mt-md">JSON</div>
    <pre>{{ JSON.stringify(initialQuery, null, 4) }}</pre>
  </div>
</template>

<script>
// @ is an alias to /src

import GroupContainer from "@/views/GroupContainer";

export default {
  name: "Home",
  components: { GroupContainer },
  data() {
    return {
      initialQuery: {
        concat: "AND",
        children: [
          {
            type: "RuleContainer",
            field: "FIELD_NAME",
            operator: "==",
            value: "VALUE",
          },
        ],
      },
    };
  },
  methods: {},
};
</script>

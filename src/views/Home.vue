<template>
  <div
    class="audience-builder query-builder-container"
    style="width: 900px; margin: 0 auto;padding: 30px"
  >
    <div class="query-builder qb-lite">
      <GroupContainer />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import GroupContainer from "@/views/GroupContainer";

export default {
  name: "Home",
  components: { GroupContainer },
  methods: {},
};
</script>

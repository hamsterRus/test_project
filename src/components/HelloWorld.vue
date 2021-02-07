<template>
  <div class="hello">
    <ul v-for="d in dir" :key="d.id">
      <li>{{ d.name }}
        <ul v-for="floder in d.under_folder" :key="floder.id">
          <li >{{ floder.name }}
            <ul v-for="files in floder.files" :key="files.id">
          <li >{{ files.name }}
          </li>
        </ul>
          </li>
        </ul>
        <ul v-for="files in d.files" :key="files.id">
          <li >{{ files.name }}
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: ["dir", "arrayItem"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

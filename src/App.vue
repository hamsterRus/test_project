<template>
  <div id="app">
    <!-- <HelloWorld :j='childJson' />
    <hr/>
    <HelloWorld :j='parentJson' />
    <hr/> -->
    <HelloWorld :dir='parentJson.data' >
    </HelloWorld>
    


    <!-- <ul>
      <li v-for="item in parentJson.data" :key="item.id">
        {{ item.name }}
        <ul>
          <li v-for="i in item.under_folder" :key="i.id">
            {{ i.name }}
            <ul>
              <li v-for="a in i.files" :key="a.id">
                {{ a.name }}
              </li>
            </ul>
          </li>
        </ul>
      </li>
    </ul> -->
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import parent from "./server/parent.json";
import child from "./server/child.json";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      parentJson: parent,
      childJson: child,
    };
  },
};
</script>

<style>

</style>

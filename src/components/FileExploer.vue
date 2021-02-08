<template>
  <div class="container">
    
    <ul v-for="d in dir" :key="d.id">
      <li>
        {{ d.name }}
        <ul v-for="floder in d.under_folder" :key="floder.id">
          <li @click.self="open">
            {{ floder.name }}
            <ul v-for="files in floder.files" :key="files.id">
              <li><a :href="files.store_name" >{{ files.name }}</a></li>
            </ul>
          </li>
        </ul>
        <ul v-for="files in d.files" :key="files.id">
          <li><a :href="files.store_name">{{ files.name }}</a></li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "FileExploer",
  props: ["dir"],

  methods: {
    open(){
      this.$emit('click-floder')
    }
  }
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul{
  padding-left: 10px;
}
li{
  list-style-type: none;
}
a{
  text-decoration: none;
}
</style>

<template>
  <div class="container" id="app">
    
    <FileExploer @click-floder="fetchData" :dir='parentJson.data' :name='nameParent' />
    <FileExploer v-if="this.childJson" :name='nameChild' :dir='childJson.data' />

  </div>
</template>

<script>
import FileExploer from "./components/FileExploer.vue";

export default {
  name: "App",
  components: {
    FileExploer,
  },
  data() {
    return {
      parentJson: '',
      childJson: '',
      nameParent: 'Папка',
      nameChild: ''
    };
  },
  mounted(){
    fetch('https://raw.githubusercontent.com/hamsterRus/test_project/master/src/server/parent.json')
      .then(res => res.json())
      .then(data => this.parentJson = data)
  },
  methods:{
    fetchData(){
      fetch('https://raw.githubusercontent.com/hamsterRus/test_project/master/src/server/child.json')
        .then(res => res.json())
        .then(data => this.childJson = data)
      this.nameChild = 'Файл'
    }
  }
};
</script>

<style lang="css">
.container{
  display: flex;
}
</style>>



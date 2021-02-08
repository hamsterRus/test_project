<template>
  <div class="container">
    <header class="header">
      <h2 class="header__title">{{ this.name }}</h2>
      <v-icon class="plus" name="plus"/>
    </header>
    <main class="content">
    <ul v-for="d in dir" :key="d.id">
      <li @click.self="open">
        <v-icon class="folder" name="folder"/>
            {{ d.name }}
        <ul v-for="floder in d.under_folder" :key="floder.id">
          <li>
            <v-icon class="folder" name="folder"/>
            {{ floder.name }}
            <ul v-for="files in floder.files" :key="files.id">
              <li  @click="pdfClick? pdfClick = false : pdfClick = true" v-if="files.name.includes('.xlsx')">
                <v-icon class="file" name="file"/>{{ files.name }}
              </li>
              <li v-if="files.name.includes('.pdf')">
               <v-icon  class="file"  name="file"/>{{ files.name }}
              </li>
            </ul>
          </li>
        </ul>
        <ul v-for="files in d.files" :key="files.id">
          <li @click="pdfClick? pdfClick = false : pdfClick = true" v-if="files.name.includes('.xlsx')">
            <v-icon  class="file" name="file"/>{{ files.name }}
          </li>
          <li v-if="files.name.includes('.pdf')">
                <pdf src="filse.store_name"><v-icon class="file" name="file"/>{{ files.name }}</pdf>
              </li>
        </ul>
      </li>
    </ul>
    <pdf v-if="pdfClick" src="/git.pdf" ref="myPdfComponent"/>
    </main>
    
  </div>
</template>

<script>
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon'
import pdf from 'vue-pdf'
export default {
  name: "FileExploer",
  props: ["dir", "name"],
  components: {
    'v-icon': Icon,
     pdf
  },
  data() {
    return {
      pdfClick: false
    };
  },

  methods: {
    open() {
      this.$emit("click-floder");
    }
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container{
  display: flex;
  flex-direction: column;
  background-color: #f0f0f0;
}
.header {
  background-color: #ffffff;
  color: white;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.header__title{
  padding-left: 50px;
  color: black;
  font-size: 14px;
}
.folder{
  color: #79b8ff;
}
.file{
  margin-right: 3px;
}
.plus{
  color: black;
  width: 7px;
}
.content{
  padding: 10px;
  border-right: 1px solid #e4e3e3;
  border-top: 1px solid #e4e3e3;
}
ul {
  padding-left: 10px;
}
li {
  list-style-type: none;
}
a {
  text-decoration: none;
}
</style>

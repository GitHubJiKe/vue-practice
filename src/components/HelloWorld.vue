<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <a href="https://www.baidu.com">百度</a><br/>
    <button @click="generatePDF">生成PDF</button>
  </div>
</template>

<script>
import html2pdf from "html2pdf.js";
export default {
  name: "HelloWorld",
  data() {
    return {};
  },
  props: {
    msg: {
      type: String,
      default: "Hello World"
    }
  },
  beforeCreate: function() {
    console.log(this.$el);
  },
  created: function() {
    console.log("this.msg:", this.msg);
  },
  methods: {
    generatePDF: function() {
      var element = document.getElementById("app");
      var option = {
        margin: 1,
        filename: "myfile.pdf",
        enableLinks: true,
        image: { type: "jpeg", quality: 1 },
        html2canvas: {
          dpi: 192,
          letterRendering: true,
          backgroundColor: "blue"
        },
        jsPDF: { unit: "in", format: "letter", orientation: "portrait" }
      };
      html2pdf(element, option);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
button {
  border: #42b983 solid 2px;
}
</style>

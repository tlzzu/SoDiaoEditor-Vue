<template>
  <div :style="{ width:width, height:height }">
     <script id="myEditor" ref="myEditor" type="text/plain">
     html内容
     </script>
  </div>
</template>

<script>
import '../../static/sde-editor/sde.config.js';
import '../../static/sde-editor/ueditor/themes/default/css/ueditor.css';
import '../../static/sde-editor/ueditor/ueditor.all.js';
import '../../static/sde-editor/ueditor/lang/zh-cn/zh-cn.js';
import '../../static/sde-editor/lang/sde-zh-cn.js';
import '../../static/sde-editor/dist/js/sde.design.js?_=123';
//设计模式
export default {
  name: 'sdeDesign',
  props: {
    //初始化配置
    config: {
      type: Object,
      default: () => {
        return {
          //id: "myEditor",
          title:
            '<div style="height: 45px;background-color: #16742B;">' +
            '<div class="left" style="position:absolute;top:0;left:0;">' +
            '<img src="/static/sde-editor/img/SoDiaoL.png" style="height:35px;margin:5px;border:none;" />' +
            '</div>' +
            '<h1 style="font-size: 14px;height: 45px;line-height: 45px;margin: 0 auto;text-align: center;font-weight: normal;color:#fff;" >SoDiaoEditor.v3.电子病历编辑器</h1>' +
            '<div style="float:right;position: absolute;top: 10px;right: 10px;">控件按钮!</div>' +
            '</div>', //自定义title
          iframe_css_src: 'static/css/iframe.css?_=9078',
          // footer: '113',
          //控件模板
          //width: 650 - 16,
          ready() {
            //debugger;
          },
          //iframe_js_src: "tonglign.css",
          print: {
            title: 'test!',
            header(index, count, page) {
              var h = document.createElement('div');
              h.style.backgroundColor = 'red';
              h.innerHTML = 'header:<br/>Page ' + (index + 1) + ' <br/>of ' + count;
              return h;
            },
            footer(index, count, page) {
              var f = document.createElement('div');
              f.innerHTML = 'footer:<br/>Page ' + (index + 1) + ' <br/>of ' + count;
              return f;
            },
            height: 1142,
            header_height: 100,
            footer_height: 45,
          },
          toolbars: {
            'sde-toolbar-file': 'file',
            'sde-toolbar-editor': ['history', 'clipboard', 'fonts', 'paragraphs'],
            'sde-toolbar-insert': [
              'horizontal',
              'spechars',
              'link',
              'img',
              'map',
              'code',
              'table',
              'formula',
              'comment',
            ],
            'sde-toolbar-tables': ['table', 'blockmergecells', 'alignmergecells'],
            'sde-toolbar-views': ['directory', 'showcomment', 'preview'],
            'sde-toolbar-tools': ['drafts', 'print', 'searchreplace', 'wordcount'],
            'sde-toolbar-records': ['sdetemplate', 'sdecontrols'],
          },
          mode: 'DESIGN',
          iframe_js_src: ['http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js'],
          controls: [
            {
              ID: 'twNum',
              VALUE: '33',
              READONLY: 1,
            },
          ], //初始化的控件值
        };
      },
    },
    width: {
      type: String,
      default: '1000px',
    },
    height: {
      type: String,
      default: '650px',
    },
  },
  data() {
    return {
      sde: null,
    };
  },
  computed: {},
  methods: {
    getHtml() {
      return this.sde.html();
    },
  },
  created() {
    console.log('sde created.');
  },
  mounted() {
    console.log('sde mounted.');
    this.config.id = 'myEditor';
    this.sde = new SDE(this.config);
  },
  beforeDestroy() {
    this.sde.__ue__.destroy();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

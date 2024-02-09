<style>
      #terminal {
        font-family: "Courier New", Courier, monospace;  
        background-color: #000;  
        color: #fff;  
        padding: 10px;  
        align-items: start;
      }
      html{
        background-color: #000;
      }
  </style>
  <div id="terminal"></div>

  <script>
      // 要逐字输出的文本
      var text =
        "\
In [1]: let Dayanshifu = EntityFactory.getEntity('Dayanshifu')\n\
0ut [1]: [Entity: Dayanshifu] \n\
            <img src='https://avatars.githubusercontent.com/u/89624700' style='border-radius:96px' width='128px' height='128px'/>\n\
            Hello! \n\
In [2]: Dayanshifu.github\n\
0ut [2]: \n\
        <img src='https://stats.deeptrain.net/user/Dayanshifu?t=20230906' width='450px' alt='code-stats'></img>\n\
In [3]: Dayanshifu.like\n\
Out [3]: [{'Frontend/App | Backend': \n\
            ['Native html/css/js', 'Python|Tk', 'Scratch']}, \n\
          'Linux Ubuntu|Arch', 'Hardware'] \n\
In [3]: Dayanshifu.Site()\n\
Out [3]: *Web server started at: '<a href='https://dayanshifu.github.io'>'https://dayanshifu.github.io'</a>\n\
In [4]: Dayanshifu.work\n\
Out [4]: {'hao-littleyan': {\n\
            'Description': '👏一个简洁方便的浏览器首页', \n\
            'Github': <a href='https://github.com/Dayanshifu/hao-littleyan'>'https://github.com/Dayanshifu/hao-littleyan'</a>, \n\
            'Site': <a href='https://dayanshifu.github.io/hao-littleyan/'>'https://dayanshifu.github.io/hao-littleyan/'</a>\n\
            }\n\
          }\n\
In [5]:";

      // 获取要显示文本的容器
      var terminal = document.getElementById("terminal");

      // 逐字显示文本
      function printText(text, i) {
        // 如果已经显示完所有字符，则退出递归
        if (i >= text.length) return;

        // 取出当前字符
        var char = text.charAt(i);

        // 创建包含当前字符的<span>标签
        var span = document.createElement("span");
        // 如果当前字符是“<”，则将后续字符视为HTML标签，直到遇到“>”
        if (char === "<") {
          var endIndex = text.indexOf(">", i);
          if (endIndex !== -1) {
            span.innerHTML = text.substring(i, endIndex + 1);
            i = endIndex;
          }
        }
        // 如果当前字符是换行符，则在HTML中换行显示
        else if (char === "\n") {
          terminal.appendChild(document.createElement("br"));
        }
        else if (char === " ") {
          span.innerHTML = "&nbsp;";
        }
        // 对于其他字符直接设置文本内容
        else {
          span.textContent = char;
        }

        // 如果当前字符是需要高亮显示的标记，添加highlight类名

        // 将<span>标签添加到容器中
        terminal.appendChild(span);

        // 使用setTimeout延迟显示下一个字符
        setTimeout(function () {
          // 递归调用printText，传入下一个字符的索引
          printText(text, i + 1);
        }, 50);
      }

      // 开始逐字显示文本
      printText(text, 0);
    </script>
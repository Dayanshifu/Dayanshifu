<style>
  #terminal {
    font-family: "Courier New", Courier, monospace;  
    background-color: #000;  
    color: #fff;  
    padding: 10px;  
    align-items: start;
  }
</style>
<div id="terminal"></div>
<script>
  // 要逐字输出的文本
  var text ="\
In [1]: let Dayanshifu = EntityFactory.getEntity('Dayanshifu')\n\
0ut [1]: [Entity: Dayanshifu] \n\
          <img src='https://avatars.githubusercontent.com/u/89624700'   style='border-radius:96px'width='128px' height='128px'/>\n\
          Hello! \n\
In [2]: Dayanshifu.github\n\
0ut [2]: \n\
        <img src='https://stats.deeptrain.net/user/Dayanshifu?t=20230906' width='550px' height='180px' style='border-radius:16px' alt='code-stats'></img>\n\
In [3]: Dayanshifu.like\n\
Out [3]: [{'Frontend/App | Backend': \n\
            ['Native html/css/js', 'Python|Tk', 'Scratch']}, \n\
          'Linux Ubuntu|Arch', 'Hardware'] \n\
In [3]: Dayanshifu.Site()\n\
Out [3]: *Web server started at: <a href='https://dayanshifu.github.io'>'https://dayanshifu.github.io'</a>\n\
In [4]: Dayanshifu.work\n\
Out [4]: {'hao-littleyan': {\n\
            'Description': '👏一个简洁方便的浏览器首页', \n\
            'Github': <a href='https://github.com/Dayanshifu/hao-littleyan'>'https://github.com/Dayanshifu/hao-littleyan'</a>, \n\
            'Site': <a href='https://dayanshifu.github.io/hao-littleyan/'>'https://dayanshifu.github.io/hao-littleyan/'</a>\n\
            }\n\
          }\n\
In [5]:";
  var terminal = document.getElementById("terminal");
  function printText(text, i) {
    if (i >= text.length) return;
    var char = text.charAt(i);
    var span = document.createElement("span");
    if (char === "<") {
      var endIndex = text.indexOf(">", i);
      if (endIndex !== -1) {
        span.innerHTML = text.substring(i, endIndex + 1);
        i = endIndex;
      }
    }
    else if (char === "\n") {
      terminal.appendChild(document.createElement("br"));
    }
    else if (char === " ") {
      span.innerHTML = "&nbsp;";
    }
    else {
      span.textContent = char;
    }
    terminal.appendChild(span);
    setTimeout(function () {
      printText(text, i + 1);
    }, 50);
  }
  printText(text, 0);
</script>

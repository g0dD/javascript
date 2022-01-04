## 浏览器

### 说下浏览器的进程、线程模型，chrome浏览器有多少个进程？线程模型中的每个线程都是干嘛用的？

浏览器是多进程的，有一个主控进程，以及每一个tab页面都会新开一个进程（某些情况下多个tab会合并进程）。
进程可能包括主控进程，插件进程，GPU，tab页（浏览器内核）等等。
  - Browser进程：浏览器的主进程（负责协调、主控），只有一个
  - 第三方插件进程：每种类型的插件对应一个进程，仅当使用该插件时才创建
  - GPU进程：最多一个，用于3D绘制
浏览器渲染进程（内核）：默认每个Tab页面一个进程，互不影响，控制页面渲染，脚本执行，事件处理等（有时候会优化，如多个空白tab会合并成一个进程）

每一个tab的进程又分为多线程
    - GUI线程
    - JS引擎线程
    - 事件触发线程
    - 定时器线程
    - 网络请求线程

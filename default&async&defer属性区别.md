## JavaScript default&async&defer属性区别
>* default
>
> 浏览器解析器在自上而下解析 HTML 标签，遇到 script 标签时会暂      停对文档其它标签的解析而读取 script 标签.
>  
* 如果 script 标签无 src 属性，为内联脚本，解析器会直接读取标签的 textContent，由 JS 解释器执行 JS 代码.
* 如果 script 有 src 属性，则从 src 指定的 URI 发起网络请求下载脚本，然后由 JS 解释器执行

---

>* async
>不会阻塞 HTML 解析器,async 脚本每个都会在下载完成后立即执行，无关 script 标签出现的顺序.

---

>* defer
>不会阻塞 HTML 解析器,defer 脚本会根据 script 标签顺序先后执行


    
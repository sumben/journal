### ES Module 101
---
> **export 可以导出任意可用的 javascript 标识符（idendifier），显式的导出方式包括声明（declaration）语句和 export { idendifier as name } 两种方式。**

---

    
    // lib/math.js
    export function sum(x, y) {
      return x + y;
    }
    export let pi = 3.141593;
    export const epsilon = Number.EPSILON;
    export { pi as PI };

在另一个文件中，使用 import ... from ... 可以导入其他模块 export 的标识符，常用的使用方式包括：

* import * as math from ... 导入整个模块，并通过 math 命名空间  调用
* import { pi, epsilon } from ... 部分导入，可直接调用 pi, epsilon 等变量


    
		// app.js
		import * as math from './lib/math.js';
		import { pi, PI, epsilon } from './lib/math.js';
		console.log(`2π = ${math.sum(math.pi, math.pi)}`);
		console.log(`epsilon = ${epsilon}`);
		console.log(`PI = ${PI}`);

---

* 只要在常规<script\>标签里，加上 type=module 属性，浏览器就会将这个脚本视为 ES 标准模块，并以模块的方式去加载、执行。
* 对于 type=module 类型的 script 标签，浏览器不再宽容。如果服务器端对远程脚本的 MIME 类型不属于有效的 JavaScript 类型，浏览器会禁止执行该脚本。
* script 标签新增了一个 nomodule 属性。已支持 type=module 的浏览器版本，应当忽略带有 nomodule 属性的 script 标签，而旧版浏览器因为不认识该属性，所以它是无意义的，不会干扰浏览器以正常的逻辑去加载 script 标签中的脚本。


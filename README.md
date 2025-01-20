# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## 运行项目

```npm
npm install
npm run dev
```

要是遇到下面这种报错：

```
X [ERROR] [plugin vite:dep-scan] Failed to resolve entry for package "vue3-video-play". The package may hav
e incorrect main/module/exports specified in its package.json: Failed to resolve entry for package "vue3-video-play". The package may have incorrect main/module/exports specified in its package.json.

    node_modules/vite/dist/node/chunks/dep-0a035c79.js:40970:10:
      40970 │     throw new Error(`Failed to resolve entry for package "${id}". ` +
            ╵           ^

    at packageEntryFailure (F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:40970:11)      
    at resolvePackageEntry (F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:40966:9)       
    at tryNodeResolve (F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:40773:20)
    at Context.resolveId (F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:40581:28)        
    at Object.resolveId (F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:39254:55)
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
    at async resolve (F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:39466:26)
    at async F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:39626:34
    at async callback (F:\桌面\saas\node_modules\esbuild\lib\main.js:933:28)
    at async handleRequest (F:\桌面\saas\node_modules\esbuild\lib\main.js:713:30)

  This error came from the "onResolve" callback registered here:

    node_modules/vite/dist/node/chunks/dep-0a035c79.js:39616:18:
      39616 │             build.onResolve({
            ╵                   ~~~~~~~~~

    at setup (F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:39616:19)
    at handlePlugins (F:\桌面\saas\node_modules\esbuild\lib\main.js:855:23)
    at Object.buildOrServe (F:\桌面\saas\node_modules\esbuild\lib\main.js:1149:7)
    at F:\桌面\saas\node_modules\esbuild\lib\main.js:2110:17
    at new Promise (<anonymous>)
    at Object.build (F:\桌面\saas\node_modules\esbuild\lib\main.js:2109:14)
    at Object.build (F:\桌面\saas\node_modules\esbuild\lib\main.js:1956:51)
    at F:\桌面\saas\node_modules\vite\dist\node\chunks\dep-0a035c79.js:39414:54
    at Array.map (<anonymous>)

  The plugin "vite:dep-scan" was triggered by this import

    script:F:/桌面/saas/src/views/CoursePlay.vue?id=0:17:26:
      17 │ import vue3VideoPlay from "vue3-video-play";
         ╵                           ~~~~~~~~~~~~~~~~~

Build failed with 1 error:
node_modules/vite/dist/node/chunks/dep-0a035c79.js:40970:10: ERROR: [plugin: vite:dep-scan] Failed to resol
ve entry for package "vue3-video-play". The package may have incorrect main/module/exports specified in its
 package.json: Failed to resolve entry for package "vue3-video-play". The package may have incorrect main/module/exports specified in its package.json.
```

问题出在 `vue3-video-play` 的 `package.json` 文件中，其 `main`、`module` 或 `exports` 字段可能配置不正确，导致 Vite 无法正确解析该包的入口文件。以下是解决方法：

**修改 `package.json` 文件**

找到项目中的 `node_modules/vue3-video-play/package.json` 文件，将其中的 `"module": "./dist/index.es.js"` 修改为 `"module": "./dist/index.mjs"`。

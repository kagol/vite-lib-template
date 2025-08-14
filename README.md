# vite-lib-template

如果你需要发布一个前端工具库，可以直接使用这个工程模板。

## 修改包名

你可以根据自己的需要修改包名，主要包括：

- vite.config.ts 文件

```typescript
export default defineConfig({
  build: {
    lib: {
      entry: resolve(__dirname, 'src/main.ts'),
      name: 'MyLib', // 建议修改成你自己的包名
      fileName: 'my-lib', // 建议修改成你自己的包名
    },
  },
})
```

- package.json 文件

```json
{
  "name": "@kagol/vite-lib-template", // 建议修改成自己的包名
  "version": "0.0.1",
  "type": "module",
  "files": ["dist"],
  "main": "./dist/my-lib.umd.cjs", // 建议修改成自己的包名
  "module": "./dist/my-lib.js", // 建议修改成自己的包名
  "exports": {
    ".": {
      "import": "./dist/my-lib.js", // 建议修改成自己的包名
      "require": "./dist/my-lib.umd.cjs" // 建议修改成自己的包名
    }
  }
}
```

## 构建发布

修改版本号，然后执行以下命令。

```shell
pnpm i
pnpm run build
pnpm publish
```

默认会包含 `es` / `umd` 两种格式的产物，可以按需配置更多形式的产物。

```diff
export default defineConfig({
  build: {
    lib: {
      entry: resolve(__dirname, 'src/main.ts'),
      name: 'MyLib', // 这是 UMD 模式，暴露在 windows 变量中的名字，可以修改成你自己的包名
      fileName: 'my-lib', // 这是产物的名字，可以修改成你自己的包名
+     format: ['es', 'cjs', 'umd']
    },
  },
})
```

## 下一步

- 给前端工具库增加基于 VitePress 的文档系统

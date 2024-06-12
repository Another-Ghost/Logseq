## 介绍
	-
- https://github.com/throw-out/puerts-unity-kit
- 目前场景中需要有一个 GameObject 具有 `Starter` 脚本。
- cd 到 tsproject 文件夹下后运行
  ``` bash
  npm run build:dev
  ```
  来启动 ts（`src` 文件夹）到 js （`output` 文件夹）的自动编译。
- [debug url](devtools://devtools/bundled/inspector.html?v8only=true&ws=127.0.0.1:9090)
- > 库中的 XOR 可能是指通过 [[CommonJS]] 和 [[ESM]] import 具体哪个 package 是通过异或的方式。
  匹配规则查看[MixerLoader.Mode](https://github.com/throw-out/puerts-unity-kit/blob/main/projects/Assets/XOR/Runtime/Src/Loader.cs)
-
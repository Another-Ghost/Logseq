alias:: Inspector

- ^^V8 Inspector^^ 是 V8 引擎内置的调试工具，它允许开发者在 [[JavaScript]] **运行时进行调试和性能分析**。可以通过 ^^V8 Inspector 协议^^与 [[JavaScript 引擎]]进行交互，支持在 [[Node.js]] 和[[浏览器]]环境中使用。
- 以下是如何在 Node.js 环境中使用 V8 Inspector 的步骤：
- ### 启动 Node.js 应用并启用 Inspector 
  logseq.order-list-type:: number
	- 在启动 Node.js 应用时，可以使用 `--inspect` 标志来启用 V8 Inspector。例如：
	  ```bash
	  node --inspect index.js
	  ```
	- 默认情况下，这将在 `localhost:9229` 上启动 Inspector。
- ### 连接到 V8 Inspector 
  logseq.order-list-type:: number
	- 有多种方式可以连接到 V8 Inspector：
	- #### 使用 Chrome DevTools
		- 打开 Chrome 浏览器。
		  logseq.order-list-type:: number
		- 输入 `chrome://inspect`。
		  logseq.order-list-type:: number
		- 在 “Devices” 部分下，点击 “Configure”。
		  logseq.order-list-type:: number
		- 确认 `localhost:9229` 在目标列表中。
		  logseq.order-list-type:: number
		- 返回 `chrome://inspect` 页面，点击 “Open dedicated DevTools for Node” 链接。
		  logseq.order-list-type:: number
	- #### 使用 `inspector` 模块
	- [[Node.js]] 提供了一个内置模块 `inspector`，可以通过代码进行连接和交互。
	  ```javascript
	  const inspector = require('inspector');
	  inspector.open(9229, 'localhost', true);
	  
	  // Your application code
	  console.log('Hello, V8 Inspector!');
	  ```
- ### 使用 Inspector 进行调试 
  logseq.order-list-type:: number
	- 一旦连接成功，你可以使用 Chrome DevTools 提供的各种调试功能，例如：
		- 设置断点
		- 查看调用堆栈
		- 检查变量
		- 分析性能
- ### 使用 V8 Inspector 进行性能分析 
  logseq.order-list-type:: number
	- 除了基本的调试功能，V8 Inspector 还可以用于性能分析。例如，捕获 CPU 性能概要：
	  ```javascript
	  const inspector = require('inspector');
	  const session = new inspector.Session();
	  session.connect();
	  
	  session.post('Profiler.enable', () => {
	  session.post('Profiler.start', () => {
	    // Your application code
	    console.log('Profiling started.');
	  
	    // 停止性能分析
	    setTimeout(() => {
	      session.post('Profiler.stop', (err, { profile }) => {
	        if (!err) {
	          require('fs').writeFileSync('profile.cpuprofile', JSON.stringify(profile));
	          console.log('Profiling completed.');
	        }
	      });
	    }, 10000); // 10 秒后停止分析
	  });
	  });
	  ```
	- 上述代码会在 10 秒后停止 CPU 分析，并将结果保存为 `profile.cpuprofile` 文件，可以在 Chrome DevTools 的 “Performance” 面板中加载和查看。
- ### 使用 TypeScript 配置 V8 Inspector 
  logseq.order-list-type:: number
	- 如果你的项目使用 TypeScript，可以安装类型定义以获得更好的开发体验：
	  ```bash
	  npm install --save-dev @types/node
	  ```
	- 然后在 TypeScript 文件中使用 `inspector` 模块：
	  ```typescript
	  import inspector from 'inspector';
	  
	  const session = new inspector.Session();
	  session.connect();
	  
	  session.post('Profiler.enable', () => {
	  session.post('Profiler.start', () => {
	    console.log('Profiling started.');
	  
	    setTimeout(() => {
	      session.post('Profiler.stop', (err, { profile }) => {
	        if (!err) {
	          require('fs').writeFileSync('profile.cpuprofile', JSON.stringify(profile));
	          console.log('Profiling completed.');
	        }
	      });
	    }, 10000);
	  });
	  });
	  ```
- ### 捕获和分析内存快照
- 内存快照可以帮助你找出应用程序中的内存泄漏和大对象。你可以使用 V8 Inspector 的 `HeapProfiler` 模块来捕获内存快照。
  ```javascript
  const inspector = require('inspector');
  const session = new inspector.Session();
  session.connect();
  
  session.post('HeapProfiler.enable', () => {
  session.post('HeapProfiler.takeHeapSnapshot', (err, { profile }) => {
    if (!err) {
      require('fs').writeFileSync('heapSnapshot.heapsnapshot', JSON.stringify(profile));
      console.log('Heap snapshot saved.');
    }
  });
  });
  ```
- 上述代码会捕获当前应用程序的内存快照，并将其保存到 `heapSnapshot.heapsnapshot` 文件中，可以在 Chrome DevTools 的 “Memory” 面板中加载和查看。
- ### 分析堆内存分配
- 你可以使用 `HeapProfiler` 模块来捕获和分析堆内存分配时间线，这有助于了解内存分配和垃圾回收的模式。
  ```javascript
  const inspector = require('inspector');
  const session = new inspector.Session();
  session.connect();
  
  session.post('HeapProfiler.enable', () => {
  session.post('HeapProfiler.startTrackingHeapObjects', () => {
    console.log('Heap tracking started.');
  
    setTimeout(() => {
      session.post('HeapProfiler.stopTrackingHeapObjects', (err, { profile }) => {
        if (!err) {
          require('fs').writeFileSync('heapProfile.json', JSON.stringify(profile));
          console.log('Heap tracking stopped.');
        }
      });
    }, 10000); // 10 秒后停止跟踪
  });
  });
  ```
- 这段代码会在 10 秒内跟踪堆内存分配，并将结果保存为 `heapProfile.json` 文件。
- ### 使用 CPU 实时分析
- 除了捕获 CPU 概要外，你还可以实时分析 CPU 使用情况。例如，捕获一段时间内的 CPU 概要：
  ```javascript
  const inspector = require('inspector');
  const session = new inspector.Session();
  session.connect();
  
  session.post('Profiler.enable', () => {
  session.post('Profiler.start', () => {
    console.log('Profiling started.');
  
    setTimeout(() => {
      session.post('Profiler.stop', (err, { profile }) => {
        if (!err) {
          require('fs').writeFileSync('profile.cpuprofile', JSON.stringify(profile));
          console.log('Profiling completed.');
        }
      });
    }, 10000); // 10 秒后停止分析
  });
  });
  ```
- ### 综合应用
- 在实际项目中，你可以结合使用这些功能，以更全面地了解应用程序的性能表现和潜在问题。例如，以下是一个综合示例，展示如何同时捕获 CPU 概要和内存快照：
  ```javascript
  const inspector = require('inspector');
  const session = new inspector.Session();
  session.connect();
  
  const captureHeapSnapshot = () => {
  session.post('HeapProfiler.enable', () => {
    session.post('HeapProfiler.takeHeapSnapshot', (err, { profile }) => {
      if (!err) {
        require('fs').writeFileSync('heapSnapshot.heapsnapshot', JSON.stringify(profile));
        console.log('Heap snapshot saved.');
      }
    });
  });
  };
  
  const captureCpuProfile = () => {
  session.post('Profiler.enable', () => {
    session.post('Profiler.start', () => {
      console.log('CPU profiling started.');
  
      setTimeout(() => {
        session.post('Profiler.stop', (err, { profile }) => {
          if (!err) {
            require('fs').writeFileSync('profile.cpuprofile', JSON.stringify(profile));
            console.log('CPU profiling completed.');
          }
        });
      }, 10000); // 10 秒后停止分析
    });
  });
  };
  
  captureHeapSnapshot();
  captureCpuProfile();
  ```
-
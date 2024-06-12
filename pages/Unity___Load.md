- 在 Unity 中，有多种加载策略可用于管理和优化资源加载。选择适当的加载策略对于确保游戏性能和用户体验至关重要。以下是一些常见的加载策略及其实现方法：
- ### 预加载 (Preloading) 
  logseq.order-list-type:: number
  预加载是指在游戏开始之前或在场景加载时一次性加载所有需要的资源。这样可以确保游戏运行时的资源访问速度，但会增加初始加载时间。
	- #### 示例：预加载资源
	  ```csharp
	  using UnityEngine;
	  
	  public class PreloadResources : MonoBehaviour
	  {
	  public string[] assetPaths; // 资源路径数组
	  private Dictionary<string, Object> loadedAssets = new Dictionary<string, Object>();
	  
	  void Start()
	  {
	      foreach (var path in assetPaths)
	      {
	          var asset = Resources.Load(path);
	          if (asset != null)
	          {
	              loadedAssets[path] = asset;
	              Debug.Log($"Preloaded asset: {path}");
	          }
	          else
	          {
	              Debug.LogWarning($"Failed to preload asset: {path}");
	          }
	      }
	  }
	  
	  public Object GetAsset(string path)
	  {
	      if (loadedAssets.ContainsKey(path))
	      {
	          return loadedAssets[path];
	      }
	      return null;
	  }
	  }
	  ```
- ### 延迟加载 (Lazy Loading) 
  logseq.order-list-type:: number
  延迟加载是在需要时才加载资源。这种方式可以减少初始加载时间，但可能会在资源首次访问时引起卡顿。
	- #### 示例：延迟加载资源
	  ```csharp
	  using UnityEngine;
	  
	  public class LazyLoadResource : MonoBehaviour
	  {
	  public string assetPath;
	  private Object asset;
	  
	  void Start()
	  {
	      // 在需要时才加载资源
	      asset = Resources.Load(assetPath);
	      if (asset != null)
	      {
	          Debug.Log($"Lazy loaded asset: {assetPath}");
	      }
	      else
	      {
	          Debug.LogWarning($"Failed to load asset: {assetPath}");
	      }
	  }
	  }
	  ```
- ### 异步加载 (Asynchronous Loading) 
  logseq.order-list-type:: number
  异步加载是在后台线程加载资源，不会阻塞主线程，从而避免加载时的卡顿。Unity 提供了 `Resources.LoadAsync` 和 `Addressables` 系统用于异步加载资源。
	- #### 示例：异步加载资源
	  ```csharp
	  using UnityEngine;
	  using System.Collections;
	  
	  public class AsyncLoadResource : MonoBehaviour
	  {
	  public string assetPath;
	  
	  void Start()
	  {
	      StartCoroutine(LoadResourceAsync(assetPath));
	  }
	  
	  IEnumerator LoadResourceAsync(string path)
	  {
	      ResourceRequest request = Resources.LoadAsync(path);
	      yield return request;
	  
	      if (request.asset != null)
	      {
	          Debug.Log($"Asynchronously loaded asset: {path}");
	      }
	      else
	      {
	          Debug.LogWarning($"Failed to asynchronously load asset: {path}");
	      }
	  }
	  }
	  ```
- ### Addressables 
  logseq.order-list-type:: number
  Addressables 是 Unity 提供的更高级的资源管理系统，支持异步加载、资源分组、依赖管理等功能。它适合处理复杂项目中的资源管理需求。
	- #### 示例：使用 Addressables 加载资源
	  首先，确保项目中已安装 Addressables 包并初始化 Addressables 系统。
	  ```csharp
	  using UnityEngine;
	  using UnityEngine.AddressableAssets;
	  using UnityEngine.ResourceManagement.AsyncOperations;
	  
	  public class AddressablesLoadExample : MonoBehaviour
	  {
	  public string assetAddress;
	  
	  void Start()
	  {
	      Addressables.LoadAssetAsync<GameObject>(assetAddress).Completed += OnAssetLoaded;
	  }
	  
	  void OnAssetLoaded(AsyncOperationHandle<GameObject> obj)
	  {
	      if (obj.Status == AsyncOperationStatus.Succeeded)
	      {
	          GameObject asset = obj.Result;
	          Debug.Log($"Addressable asset loaded: {asset.name}");
	      }
	      else
	      {
	          Debug.LogWarning("Failed to load addressable asset.");
	      }
	  }
	  }
	  ```
- ### 资源包 (Asset Bundles) 
  logseq.order-list-type:: number
  Asset Bundles 是 Unity 提供的一种资源打包和分发方式，可以将资源打包成一个个 bundle，在需要时加载这些 bundle 来获取资源。Asset Bundles 适合用于 DLC、更新包等。
	- #### 示例：加载 Asset Bundle
	  ```csharp
	  using UnityEngine;
	  using System.Collections;
	  
	  public class LoadAssetBundleExample : MonoBehaviour
	  {
	  public string bundleURL;
	  public string assetName;
	  
	  IEnumerator Start()
	  {
	      using (WWW www = WWW.LoadFromCacheOrDownload(bundleURL, 0))
	      {
	          yield return www;
	  
	          if (www.error != null)
	          {
	              Debug.LogError($"Failed to download asset bundle: {www.error}");
	              yield break;
	          }
	  
	          AssetBundle bundle = www.assetBundle;
	          if (bundle != null)
	          {
	              GameObject asset = bundle.LoadAsset<GameObject>(assetName);
	              if (asset != null)
	              {
	                  Instantiate(asset);
	              }
	              else
	              {
	                  Debug.LogWarning("Failed to load asset from bundle.");
	              }
	  
	              bundle.Unload(false);
	          }
	      }
	  }
	  }
	  ```
- ### 内存管理 
  logseq.order-list-type:: number
  为了避免内存泄漏和高内存占用，应该在适当的时候卸载不再使用的资源。例如，使用 `Resources.UnloadUnusedAssets` 或 `Addressables.Release`。
	- #### 示例：卸载资源
	  ```csharp
	  using UnityEngine;
	  
	  public class UnloadUnusedAssetsExample : MonoBehaviour
	  {
	  void Start()
	  {
	      Resources.UnloadUnusedAssets();
	  }
	  }
	  ```
- ### 总结
  根据项目的具体需求，选择适当的加载策略可以显著提升游戏性能和用户体验。以下是一些指导原则：
	- **预加载**：适合需要立即访问的关键资源，但会增加初始加载时间。
	  logseq.order-list-type:: number
	- **延迟加载**：适合非关键资源，可以减小初始加载时间，但可能会导致首次访问时的卡顿。
	  logseq.order-list-type:: number
	- **异步加载**：避免加载时的卡顿，适合大型资源或需要动态加载的场景。
	  logseq.order-list-type:: number
	- **Addressables**：适合复杂项目中的资源管理，提供灵活的资源分组和加载机制。
	  logseq.order-list-type:: number
	- **Asset Bundles**：适合DLC、更新包等，需要打包和分发的资源。
	  logseq.order-list-type:: number
	- **内存管理**：及时卸载不再使用的资源，以控制内存占用。
	  logseq.order-list-type:: number
	  通过综合运用这些加载策略，可以优化资源加载过程，提高游戏性能，提供更好的用户体验。
	  <!--Converted by ToLogseq-->
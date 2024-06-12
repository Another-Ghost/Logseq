- LZMA 和 [[LZ4]] 是两种常见的[[压缩算法]]，它们在 Unity 中主要用于压缩和解压缩 [[Asset Bundles]] 以优化资源加载时间和内存使用。以下是它们的详细介绍和在 Unity 中的应用。
- ### LZMA
	- #### 特点
		- **高压缩比**：LZMA（Lempel-Ziv-Markov Chain Algorithm）是一种压缩率很高的算法，通常可以显著减少文件大小。
		- **较慢的压缩和解压速度**：LZMA 的压缩和解压速度相对较慢，尤其是在资源较大的情况下。
	- #### 使用场景
		- **初次下载和安装**：由于 LZMA 提供了高压缩比，因此非常适合在游戏的初次下载和安装过程中使用，以减少下载文件的大小。
		- **离线存储**：LZMA 适合用于长时间存储的资源包，因为其高压缩率可以节省存储空间。
- ### [[LZ4]]
	- #### 特点
		- **快速压缩和解压速度**：LZ4 是一种速度非常快的压缩算法，尽管其压缩比不如 LZMA 高，但在解压速度上有显著优势。
		- **较低的压缩比**：相比 LZMA，LZ4 的压缩比略低，但其快速的解压速度弥补了这一不足。
	- #### 使用场景
		- **实时加载**：LZ4 非常适合需要快速加载的场景，如游戏运行时需要动态加载的资源，因为其解压速度非常快。
		- **频繁访问的资源**：对于需要频繁访问和解压的资源，使用 LZ4 可以显著提高加载性能。
- ### 在 Unity 中的应用
  在 Unity 中，您可以在打包 Asset Bundle 时选择使用 LZMA 或 LZ4 压缩算法。以下是如何使用这两种压缩算法的示例。
	- #### 使用 LZMA 压缩
	  LZMA 通常用于初次打包和分发阶段，以减小资源包的大小。打包时默认使用 LZMA 压缩。
	  ```csharp
	  using UnityEditor;
	  using UnityEngine;
	  
	  public class BuildAssetBundles
	  {
	  [MenuItem("Assets/Build AssetBundles LZMA")]
	  static void BuildAllAssetBundlesLZMA()
	  {
	      // 设置 AssetBundle 的输出路径
	      string assetBundleDirectory = "Assets/AssetBundles";
	      if (!System.IO.Directory.Exists(assetBundleDirectory))
	      {
	          System.IO.Directory.CreateDirectory(assetBundleDirectory);
	      }
	  
	      // 使用 LZMA 压缩打包
	      BuildPipeline.BuildAssetBundles(assetBundleDirectory,
	                                      BuildAssetBundleOptions.None,
	                                      BuildTarget.StandaloneWindows);
	  }
	  }
	  ```
	- #### 使用 LZ4 压缩
	  LZ4 通常用于游戏运行时的加载阶段，以加快资源的加载速度。可以在打包时指定使用 LZ4 压缩。
	  ```csharp
	  using UnityEditor;
	  using UnityEngine;
	  
	  public class BuildAssetBundles
	  {
	  [MenuItem("Assets/Build AssetBundles LZ4")]
	  static void BuildAllAssetBundlesLZ4()
	  {
	      // 设置 AssetBundle 的输出路径
	      string assetBundleDirectory = "Assets/AssetBundles";
	      if (!System.IO.Directory.Exists(assetBundleDirectory))
	      {
	          System.IO.Directory.CreateDirectory(assetBundleDirectory);
	      }
	  
	      // 使用 LZ4 压缩打包
	      BuildPipeline.BuildAssetBundles(assetBundleDirectory,
	                                      BuildAssetBundleOptions.ChunkBasedCompression,
	                                      BuildTarget.StandaloneWindows);
	  }
	  }
	  ```
- ### 解压 Asset Bundle
  在 Unity 中加载和解压 Asset Bundle 可以使用 [[UnityWebRequest]]。
	- #### 加载和解压 LZ4 Asset Bundle
	  ```csharp
	  using UnityEngine;
	  using UnityEngine.Networking;
	  using System.Collections;
	  
	  public class LoadAssetBundleExample : MonoBehaviour
	  {
	  IEnumerator Start()
	  {
	      string url = "file:///" + Application.dataPath + "/AssetBundles/mybundle";
	      UnityWebRequest www = UnityWebRequestAssetBundle.GetAssetBundle(url);
	      yield return www.SendWebRequest();
	  
	      if (www.result != UnityWebRequest.Result.Success)
	      {
	          Debug.LogError(www.error);
	      }
	      else
	      {
	          AssetBundle bundle = DownloadHandlerAssetBundle.GetContent(www);
	          if (bundle != null)
	          {
	              // 从 Asset Bundle 中加载资源
	              GameObject obj = bundle.LoadAsset<GameObject>("MyPrefab");
	              Instantiate(obj);
	          }
	          else
	          {
	              Debug.LogError("Failed to load AssetBundle");
	          }
	      }
	  }
	  }
	  ```
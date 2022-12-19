# DalamudPluginsD17

你好！ 这是 [Final Fantasy XIV 的 Dalamud 插件框架](https://github.com/ottercorp/Dalamud) 的插件库。 此存储库是 [DalamudPlugins](https://github.com/ottercorp/DalamudPlugins) 的继承者并实现了 [DIP17](https://github.com/goatcorp/DIPs/blob/main/text/17-automated-build-and-submit-pipeline.md) 使提交过程更容易和更快。

## 发布你的插件

### 准备你的仓库

- 确保您的插件位于可公开访问的 Git 存储库中（GitHub、GitLab、任何允许 HTTP 克隆而无需身份验证的自托管 Git 实例）
- 更新你的 .csproj
   - 在 "PropertyGroup" 中设置 "<RestorePackagesWithLockFile>true</RestorePackagesWithLockFile>"
   - 如果您还没有使用 `$(DalamudLibPath)`，请参阅 <https://github.com/goatcorp/SamplePlugin/blob/master/SamplePlugin/SamplePlugin.csproj#L29-L63>
- 在 Release 中构建你的插件，提交你的 `.csproj` + 新生成的 lock 文件

### 提交

- 分叉此存储库，或使用 GitHub 网络编辑器（在存储库中按 `.`，或按现有清单上的 ✏ 图标）
- 在你的 fork 中，制作 `stable/(plugin name)/manifest.toml`（或 `testing/live/(plugin name)/manifest.toml` - 请注意，我们更喜欢新插件进入 `testing/live`， 以便在向更广泛的受众传播之前解决皱纹问题）。 有关更多信息，[参见此处](https://github.com/goatcorp/DIPs/blob/main/text/17-automated-build-and-submit-pipeline.md#guide-level-explanation)。
- 请注意，请确保您的用户名在 `owners` 中，即便您只是将插件进行了国服适配（例如下面的`owners = ["goaaats", "Bluefissure"]`）。

  ```toml
  [plugin]
  repository = "https://github.com/goatcorp/SamplePlugin.git"
  commit = "765d9bb434ac99a27e9a3f2ba0a555b55fe6269d"
  owners = ["goaaats", "Bluefissure"]
  project_path = "SamplePlugin"
  changelog = "Added Herobrine"
  ```
  
- 将插件的图像放在 `images` 子文件夹中：`stable/（插件名称）/images`。
   - 请注意，这将 [在未来的某个时候进行简化](https://github.com/goatcorp/DIPs/pull/45)。 这尚未[实施](https://github.com/goatcorp/DalamudPackager/issues/9)。 如果您能提供帮助，我们很乐意听取您的意见！
- 创建 PR。 如果您使用的是 GitHub 网络编辑器，这将是自动的。

您还需要使用 DalamudPackager； 请查看 SamplePlugin 示例。 如果您需要帮助，请联系我们。

## 更新你的插件

只需编辑清单中的提交 commit 的哈希（sha256）。 请始终从新分支进行更新，以便我们进行更清晰的审核。

## 在 PR 中重建

如果你想触发你的 PR 的重建，只需发表一条内容为 `@aonyx rebuild` 的评论。

---

提交插件时，请考虑我们的 [可接受使用政策](<https://github.com/goatcorp/FFXIVQuickLauncher/wiki/Acceptable-Use-Policy-(Official-Plugin-Repository)>) 和 [服务条款](<https://github.com/goatcorp/FFXIVQuickLauncher/wiki/Terms-and-Conditions-of-Use-(XIVLauncher,-Dalamud-&-Official-Plugin-Repository)>)，例如详细说明将插件上传到此存储库时您需要授予我们的权利。

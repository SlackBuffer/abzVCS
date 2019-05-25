<!-- http://www.ituring.com.cn/book/1581 -->
- Config
	
    ```bash
    git config --global user.name "Firstname Lastname"
    git config --global user.email "your_email@example.com"
    git config --global color.ui auto
    cat `~/.gitconfig`

    # 创建、添加公钥后测试通信
    ssh -T git@github.com
    ```

- README.md
    - 软件的概要、使用流程、许可协议等
## Git
- 暂存区（Stage, Index）
- `git log`
	
    ```bash
    git log --pretty-short
    git log fileName/Dir
    git log --graph
    ```

- `git diff`
	
    ```bash
    # 工作区与暂存区（暂存区无内容则显示与最新提交状态之间的差别）
    git diff
    # 工作区与提交的差别
    git diff commitID
    ## 与最新提交的差别
    git diff HEAD
    ```

### 分支
- `git branch` 显示分支
    - `*` 表示当前所在分支
- 命令

    ```bash
    git checkout -b feature_A
    # git branch feature_A
    # git checkout feature_A

    # 切换回上一个分支
    git checkout -
    ```

- **特性分支**是集中实现单一特性（主题），除此之外不进行任何作业的分支
    - 如 `feature_A` 分支，这一分支主要实现特性 A，除特性 A 的实现之外不进行任何作业
    - 即便在开发过程中发现了 BUG，也需要再创建新的分支，在新分支中进行修正
- 在日常开发中，往往会创建数个特性分支，同时在此之外再保留一个随时可以发布软件的稳定分支
    - 稳定分支的角色通常由 `master` 分支担当
- 基于特定主题的作业在特性分支中进行，主题完成后再与 `master` 分支合并
    - 保持这样一个开发流程，就能保证 `master` 分支没有开发一般的代码，可以随时供人查看，其他开发者也可以放心大胆地从 `master` 分支创建新的特性分支
- **主干分支**是特性分支的原点，同时也是合并的终点
    - 通常人们会用 `master` 分支作为主干分支
    - 主干分支中并没有开发到一半的代码，可以随时供他人查看
- 有时我们需要让这个主干分支总是配置在正式环境中，有时又需要用标签 Tag 等创建版本信息，同时管理多个版本发布
    - 拥有多个版本发布时，主干分支也有多个
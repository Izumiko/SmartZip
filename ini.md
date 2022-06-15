## INI设置
- 直接运行 `SmartZip.exe` 会弹出设置
- 推荐设置
    - 清空 `password rename delete` 节下所有内容,按需求添加
    - 在 `menu` 节下按需求启用单个右键菜单
- 源 被解压或被压缩的文件
- 目标 解压或压缩后的文件
- 值 设定的值
    - `<--->` 分为两部分,用左,右表示
- 键(key) 示例 `7zipDir`
    - `...` 表示其为递增
- 节(section) 示例 `[set]`
- 节名称以 `Exp` 结尾代表其为 正则表达式
    - `extExp`
    - `源后缀名 ~= 值` 表示 源后缀名 匹配 值
- 如说明含有启用或禁用,则默认 `0`禁用,`1`启用
- 键以数字为名称表示其可自行增加,从`1`开始
    - 比方说密码为`1-7`,如需新增在当前节`password`添加 `8,9,10...`
- 相对路径 `%SmartZipDir%` ,它表示`SmartZip.exe`所在的文件夹,不包含最后的`\`


| 键(key) | 节(section) | 版本 | 默认值 | 说明 | 示例/更多说明 |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 7zipDir  | set | 2.0(0) | %SmartZipDir%\7-zip | 7-zip所在文件夹 |
| successPercent  | set | 2.0(0) | 10 `MB` | 判断是否解压成功 | `源大小 - 目标大小 > 源大小 * 10%` |
| successMinSize  | set | 2.12(10) | 10 `KB` | 判断是否解压成功 | `源大小 < 10kb` (可测试压缩只有一个链接的txt比较大小)
| delSource  | set | 2.0(0) | 0 | 启用解压成功删除源文件 | 嵌套压缩包总是会被删除
| delWhenHasPass  | set | 2.0(0) | 0 | 启用源包含密码时解压成功删除源文件 | 此项不必启用`delSource`
| logLevel  | set | 2.0(0) | 5 | 操作日志等级 0-5 | 依次为 禁用日志,删除,重命名,命令行错误,命令行正确,其他
| cmdLog  | set | 2.11(9) | 0 | 启用测试日志 | 启用可在当前目录查看 __SmartZipCmdLog.txt
| icon  | set | 2.0(0) | %SmartZipDir%\ico.ico | 右键菜单,托盘,界面的图标 | 为空时其为 7-zip 的图标
| hideRunSize  | set | 2.11(9) | 10 `MB` | 源大小 `<` `值`时隐藏界面运行 | 无干扰但稍慢 `0-100ms`
| muiltNesting  | set | 2.11(9) | 0 | 启用多文件嵌套解压 | 单文件嵌套总是会被解压
| version  | set | 2.11(12) | 当前内部版本号 | 标识内部版本号 | 用来新增新版本ini,无需理会
| 1,2,3...  | password | 2.0(0) | 密码... | 如源有密码遍历密码,成功解压 | 按顺序遍历(把常用的添加在前面)
| lastPass  | password | 2.0(0) | 最后使用的密码 | 无需理会
| 1,2,3...  | ext | 2.0(0) | `zip`... | 源后缀名`=` `值`表示其为压缩包 | 会在打开或解压时判断
| 1,2,3...  | extExp | 2.0(0) | `^\d+$`... | 源后缀名`~=` `值`表示其可能为压缩包 | 会在解压时判断
| 1,2,3...  | extForOpen | 2.0(0) | `iso`... | 源后缀名`=` `值`表示其可作为压缩包打开 | 会在打开时判断
| 1,2,3...  | renameExt | 2.0(0) | `mp+3<--->mp3`... | 解压后文件后缀名`=` `左`时改名 | 替换 `mp+3` 为 `mp3`
| 1,2,3...  | renameName | 2.0(0) | `666666-<--->`... | 解压后文件名`包含` `左`时改名 | 替换 `666666` 为 空
| 1,2,3...  | renameExp | 2.0(0) | `^[ 	]+<--->`... | 解压后文件名`~=` `左`时改名 | 替换 文件名首部空白字符 为 空
| 1,2,3...  | deleteExt | 2.0(0) | ... | 解压后文件后缀名`=` `左`时删除
| 1,2,3...  | deleteName | 2.0(0) | ... | 解压后文件后名`包含` `左`时删除
| 1,2,3...  | deleteExp | 2.0(0) | ... | 解压后文件名`~=` `左`时删除
| 1,2,3...  | unZipCheckError | 2.0(0) | `ERROR:<--->10`... | 命令行`匹配` `左` `右`次提示输入密码 | 匹配 `ERROR:` `10` 次
| 1,2,3...  | unZipCheckErrorExp | 2.0(0) | ... | 命令行`~=` `左` `右`次提示输入密码 | 启用`cmdLog`后可查看命令行
| 1,2,3...  | unZipCheckErrorContinueExP | 2.0(0) |  | 命令行`~=` `左` `右`次跳过此项 | 它不是压缩包
| 1,2,3...  | unZipCheckSuccess | 2.0(0) | ... | 命令行`匹配` `左` `右`次解压 | 密码正确或无需密码
| 1,2,3...  | unZipCheckSuccessExp | 2.0(0) | ... | 命令行`~=` `左` `右`次解压 | 此类型可启用`cmdLog`查看内容
| 1,2,3...  | openZipCheckError | 2.0(0) | ... | 用于打开的判断,同上
| 1,2,3...  | openZipCheckErrorExp | 2.0(0) | ... | 同上
| 1,2,3...  | openZipCheckSuccess | 2.0(0) | ... | 同上
| 1,2,3...  | openZipCheckSuccessExp | 2.0(0) | ... | 同上
| openAdd  | 7z | 2.0(0) | .zip" -tzip -mx=0 -aou -ad | 7-zip新建压缩包默认参数 | 执行`o`时(用7-zip打开非压缩文件)
| add  | 7z | 2.0(0) | .zip" -tzip -mx=0 -aou -ad | 压缩默认参数 | 执行`a`时(压缩)
| openZip  | menu | 2.0(0) | 1 | 启用`o`右键菜单
| openZipName  | menu | 2.0(0) | 用7-Zip打开 | `o`右键菜单名称
| unZip  | menu | 2.0(0) | 1 | 启用`x`右键菜单
| unZipName  | menu | 2.0(0) | 智能解压 | `x`右键菜单名称
| addZip  | menu | 2.0(0) | 1 | 启用`a`右键菜单
| addZipName  | menu | 2.0(0) | 压缩 | `a`右键菜单名称
| isLoop  | temp | 2.0(0) |  | 正在解压嵌套文件 | 无需理会
| guiShow  | temp | 2.0(0) |  | GUI显示状态 | 无需理会
| addCurrentDir2Pass | personalized | 2.14(12) | 0 | 启用把当前文件夹名称加入密码列表 | 此节一般是特殊需求,一般无需理会
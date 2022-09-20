# LaTeX Template for ActaPhysicaSinica (物理学报)

## 物理学报（Acta Physica Sinica）的LaTeX模板

由于物理学报官网给的LaTeX模板是基于CTeX书写的并且已经多年未更新，我重写了新的sty文件，使之可以正常使用。
在TeX Live 2022 和 TeX Live 2021上测试，可运行无误

****此模板默认的参考文献格式与物理学报稍有不同，模板使用GB/T 7714格式，物理学报使用自有格式，如需严格符合要求，请使用工具自定义BibTex的style文件，欢迎上传符合要求的bib样式文件****

****物理学报要求图、表标题使用双语标题，建议文中图表标题使用命令`\bicaption{ <中文标题> }{ <英文标题> }`****


## 文档和说明：
          

***notes:用 `<text>` `<contents>` 等表示具体的一段内容或文字***

### 颜色相关

- 预定义的颜色 

    [red, blue, yellow, white]

- 设置字体颜色 

    `\Red{<文字>} \Blue{..} \Yellow{..} \White{..}`

- 高亮一段文字（黄底白框红字） 

    `\highlight{<文字>}`

### 一些方便的小命令

 - 段首空两格的“两个空格” (两个 `\quad` 长度的空白)

    `\indt`  

 - 整段缩进 （一个没有项目符号的itemize环境）

    `\pindt{ <一段文字> }`

 - 全微分符号 d 

    `\D`  

    - 可独立使用，也可用在  数学模式$<>$中

 - 图像占位符 

    `\hpic[ <caption> ] `
    - `<caption> 默认值 = HERE'S A PICTURE`
    - 草稿中临时替代图像，显示为高亮的 `<caption>` 
    - 如果给定 `<caption>`，则占位符具有 `label = fig:<caption>`

 - 化学式 （正体的数学模式）

    `\chem{ <化学式> }`
    - 可独立使用  也可用在  数学模式
    - $\rm H_2O$ == `\chem{H_2O}` == `$\chem{H_2O}$`

 - 按照行距和磅数设置字体大小

    `\setfontsize{ <字号/磅> }[ <行距/倍> ]`
    - `<行距> 默认值 = 1.5`

### 标题、作者、摘要、关键词 和 PACS 

 - 标题变量的赋值

    `\title[ <English Title> ]{ <中文标题> }`
    - 将中英文标题储存，以供\maketitle命令使用
    - 当 `<Englsih Title>` 未指定时，英文部分显示为`-NoValue-`

 - 作者变量的赋值

    `\author[ <English Author List> ]{ <作者列表> }`
    - `<content>` 中可用 `\and `命令分隔作者名，作用为 `\quad `
    - `<content>` 中可用 `\superscript{ <上标> }` 命令产生上标
    - `David\superscript{ \dagger } `
    - `<上标>` 处于数学模式中

 - 所在单位变量赋值

    `\institude[ <English Institude List> ]{ <单位列表> } `

 - 创建标题 maketitle 

    `\maketitle `
    - 第一次使用` \maketitle `时，产生中文标题部分 `<中文xxx>`；
    - 第二次使用，产生英文标题部分 `<English xxx>`
    - 标题部分包括 标题、作者、单位 

 - 摘要 

    ```latex
        \abstract[ <英文开关> ]{ <摘要内容> }
    ```

    ```latex
        \begin{abstract}[ <英文开关> ]
            <摘要内容>
        \end{abstract}
    ```

    - 函数式写法 和 环境式写法 效果完全相同

    - `<英文开关> = [  english=true ,  english=false ,  english ]`
    -  默认值 =  `english=false` 
    -   `english`  等同于  `english=true `
    - `\abstract{}` 产生中文部分， `\abstract[english]{}` 产生英文部分
    - 中文摘要 显示 “摘要” ，英文摘要显示 "Abstract" 

 - 关键词

    `\keywords[ <英文开关> ]{ <关键词> }`

    - `<英文开关>` 与` \abstract` 相同

    - `\keywords` 结束后需要自行换行

 - PACS代码

    `\pacs `

    - 需要自行换行

 - 基金
   
    `\fund[ <英文开关> ]{ <基金内容> }` 
    
    - `<英文开关>` 与` \abstract` 相同

 - 邮箱
   
    `\email[ <作者类型> ]{ <邮箱地址> }` 

    - `<作者类型>` 即： 通讯作者、第一作者、第二作者 ......

    - `<作者类型>` 省略时**默认**为**通讯作者**，通讯作者前有 $\dagger$ 符号
    
 - 致谢
  
    `\acknowledgement{ <内容> }`

 - 附录

    `\appendix[ <新页面开关> ]`

    - `<新页面开关>` 
       - 新一页  `newpage=true`  or ` newpage `；
       - 当前位置 ` newpage=false `；
       - 默认值 `false` 当前位置；

    - 显示效果为 `附录 A` `附录 B` `附录 C` ...
       - 每次使用此命令，附录二字后编号自动向后迭代（最多可到 Z ） 
       
    - **此命令后的figure、table表格标题自动附带附录序号**，如 `表 A1` `图 B2`

### bib参考文献 

 - 导入bib文件

    `\bibreference[ <可选控制参数> ]{ <bib文件名> }`

    - 导入的bib文件自动按 GB-T 7714 格式排版 

    - `<可选控制参数>` 包含：
       - `nocite` 导入bib中所有文献 或 只导入前文使用过的文献
           - 导入全部 `nocite=true ` or  `nocite`； 
           - 使用过的 `nocite=false `；
           - 默认值 `true` 导入全部
       - `newpage` 在新一页放置参考文献 或 在当前位置开始文献
           - 新一页  `newpage=true`  or ` newpage `；
           - 当前位置 ` newpage=false `；
           - 默认值 `false` 当前位置；
       - `style` 参考文献排序方式 `[引用顺序, 作者名-年份]`
           - 引用顺序 ` style=numerical `；

               有数字序号，按照引用顺序和bib中顺序排序

           - 作者名-年份 ` style=author-year ` 

                无序号，按照作者名字和年份联合排序

           - 默认值 `numerical` 按引用顺序排序  




### 导入的一些包 

 - 双语标题 from package  `bicaption`

    `\bicaption{ <caption 1> }{ <caption 2> }`

 - 版面设置 from package `geometry`

    `\geometry{ <key-val specifier> } `

 - 多栏排版 from package ?

    `\setlength\columnsep{<栏间距>}`

 - 多栏 from package `multicols`

    ```latex
    \begin{multicols}{<栏数目>}
        <contents>  
    \end{multicols}  
    ```

    


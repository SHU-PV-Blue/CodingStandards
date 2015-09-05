# 光伏蓝队 C#编码规范 #
## 一、命名规则 ##

### 1.1 命名的基本约定 ###

1. 要使用可以准确说明变量/字段/类的完整的英文描述符，如firstName。对一些作用显而易见的变量可以采用简单的命名，如在循环里的递增（减）变量就可以被命名为 “i”。
2. 要尽量采用项目所涉及领域的术语。
3. 要采用大小写混合，提高名字的可读性。为区分一个标识符中的多个单词，把标识符中的部分单词的首字母大写。**不采用下划线作分隔字符的写法。**   
有两种适合的书写方法，适应于不同类型的标识符：   
**帕斯卡命名法**：标识符的每一个单词的首字母都大写；   
**骆驼命名法**：除第一个单词之外，标识符的其他单词首字母大写。   
4. 避免使用缩写，如果一定要使用，就谨慎使用。同时，应该保留一个标准缩写的列表，并且在使用时保持一致。   
5. 对常见缩略词，两个字母的缩写要采用统一大小写的方式（示例：ioStream，getIOStream）；多字母缩写采用首字母大写，其他字母小写的方式（示例：getHtmlTag）；   
6. 避免使用长名字（最好不超过 15 个字母）； 
7. 避免使用相似或者仅在大小写上有区别的名字；
8. 私有字段因其具有对内的全局性和对外的不可见性，需加下划线做前缀以示强调。

下表描述了不同类型标识符的大小写规则：   
<table>
   <tr>
      <td>标识符</td>
      <td>命名法</td>
      <td>示例</td>
   </tr>
   <tr>
      <td>命名空间</td>
      <td>帕斯卡命名法</td>
      <td>namespace Com.Techstar.ProductionCenter</td>
   </tr>
   <tr>
      <td>类型</td>
      <td>帕斯卡命名法</td>
      <td>public class DevsList</td>
   </tr>
   <tr>
      <td>接口</td>
      <td>帕斯卡命名法</td>
      <td>public interface ITableModel</td>
   </tr>
   <tr>
      <td>方法</td>
      <td>帕斯卡命名法</td>
      <td>public void UpdateData()</td>
   </tr>
   <tr>
      <td>属性</td>
      <td>帕斯卡命名法</td>
      <td>Public int Length{…}</td>
   </tr>
   <tr>
      <td>事件</td>
      <td>帕斯卡命名法</td>
      <td>public event EventHandler Changed;</td>
   </tr>
   <tr>
      <td>私有字段</td>
      <td>驼峰命名法</td>
      <td>private string _fieldName;</td>
   </tr>
   <tr>
      <td>非私有字段</td>
      <td>帕斯卡命名法</td>
      <td>public string FieldName；</td>
   </tr>
   <tr>
      <td>枚举值</td>
      <td>帕斯卡命名法</td>
      <td>FileMode{Append}</td>
   </tr>
   <tr>
      <td>参数</td>
      <td>驼峰命名法</td>
      <td>public void UpdateData(string fieldName)</td>
   </tr>
   <tr>
      <td>局部变量</td>
      <td>驼峰命名法</td>
      <td>string fieldName;</td>
   </tr>
</table>
 
### 1.2 各种标示符类型的命名约定 ###

#### 1.2.1 程序集命名 ####

实验室名称（Lab）+ 项目名称 + 模块名称（可选），例如：
中心服务器程序集：Lab.SeverCenter；
中心服务器业务逻辑程序集：Lab.SeverCenter.Business；

#### 1.2.2 命名空间命名 ####

采用和程序集命名相同的方式：实验室名称（Lab）+ 项目名称 + 模块名称。 另外，一般情况下建议命名空间和目录结构相同。例如：
中心服务器：Lab.SeverCenter；
中心服务器下的用户控件：Lab.SeverCenter.UserControl；
中心服务器业务逻辑：Lab.SeverCenter.Business；
中心服务器数据访问：Lab.SeverCenter.Data；

#### 1.2.3 程序集和DLL ####

大多数情况下，程序集包含全部或部分可重用库，且它包含在单个动态链接库(DLL) 中。
一个程序集可拆分到多个DLL 中，但这非常少见，在此准则中也没有说明。
程序集和DLL 是库的物理组织，而命名空间是逻辑组织，其构成应与程序集的组织无关。
命名空间可以且经常跨越多个程序集。可以考虑如下模式命名DLL：
`<Company>.<Component>.dll`
例：`Lab.SeverCenter.dll`
 
#### 1.2.4 类和接口命名 ####

1. 类的名字要用名词；
2. 避免使用单词的缩写，除非它的缩写已经广为人知，如HTTP。
3. 接口的名字要以字母I开头。保证对接口的标准实现名字只相差一个“I”前缀，例如对IComponent接口的标准实现为Component；
4. 泛型类型参数的命名：命名要为T或者以T开头的描述性名字，例如：   
　　　　`public class List<T>`   
　　　　`public class MyClass<Tsession>`   
5. 对同一项目的不同命名空间中的类，命名避免重复。避免引用时的冲突和混淆；

#### 1.2.5 方法命名 ####

1. 第一个单词一般是动词；
2. 如果方法返回一个成员变量的值，方法名一般为Get+成员变量名，如若返回的值 是bool变量，一般以Is作为前缀。另外，如果必要，考虑用属性来替代方法；
3. 如果方法修改一个成员变量的值，方法名一般为：Set + 成员变量名。同上，考虑 用属性来替代方法。

#### 1.2.6 变量命名 ####

1. 按照使用范围来分，我们代码中的变量的基本上有以下几种类型：类的公有变量；类的私有变量；方法的参数变量；方法内部使用的局部变量。这些变量的命名规则基本相同，见标识符大小写对照表。区别如下：   
　　　　a) 类的公有变量按帕斯卡命名法命名，无特殊要求；   
　　　　b) 类的私有变量采用驼峰命名法，需加采用加下划线前缀，例如_workerName;   
　　　　c) 方法的参数变量采用驼峰命名法，例如workerName；   
2. 方法内部的局部变量采用驼峰命名法，例如workerName。
3. 尽量要使用短而且具有意义的单词；
4. 单字符的变量名一般只用于生命期非常短暂的变量：i,j,k,m,n一般用于integer；c,d,e 一般用于characters；s用于string
5. 如果变量是集合，则变量名要用复数。例如表格的行数，命名应为：RowsCount；
6. 命名组件要采用匈牙利命名法，所有前缀均应遵循同一个组件名称缩写列表。
 
### 1.3  组件类型缩写列表 ###

匈牙利命名法的基本原则是：变量名=属性+类型+对象描述，这里将其简化为：组件示例名=组件类型缩写+组件描述。描述缩写的基本原则是取组件类名各单词的第一个字母，如果只有一个单词，则去掉其中的元音，留下辅音。缩写全部为小写。下表列举了一些常见组件的类型缩写以及命名示例：
<table>
   <tr>
      <td>组件类型</td>
      <td>缩写</td>
      <td>例子</td>
   </tr>
   <tr>
      <td>Form</td>
      <td>Frm</td>
      <td>frmMenu</td>
   </tr>
   <tr>
      <td>Label</td>
      <td>Lbl</td>
      <td>lblNote</td>
   </tr>
   <tr>
      <td>TextBox</td>
      <td>Txt</td>
      <td>txtName</td>
   </tr>
   <tr>
      <td>Button</td>
      <td>Btn</td>
      <td>btnOK</td>
   </tr>
   <tr>
      <td>ImageButton</td>
      <td>Ib</td>
      <td>ibOK</td>
   </tr>
   <tr>
      <td>LinkButton</td>
      <td>Lb</td>
      <td>lbJump</td>
   </tr>
   <tr>
      <td>HyperLink</td>
      <td>Hl</td>
      <td>hlJump</td>
   </tr>
   <tr>
      <td>DropDownList</td>
      <td>Ddl</td>
      <td>ddlList</td>
   </tr>
   <tr>
      <td>CheckBox</td>
      <td>Cb</td>
      <td>cbChoice</td>
   </tr>
   <tr>
      <td>CheckBoxList</td>
      <td>Cbl</td>
      <td>cblGroup</td>
   </tr>
   <tr>
      <td>RadioButton</td>
      <td>Rb</td>
      <td>rbChoice</td>
   </tr>
   <tr>
      <td>RadioButtonList</td>
      <td>Rbl</td>
      <td>rblGroup</td>
   </tr>
   <tr>
      <td>Image</td>
      <td>Img</td>
      <td>imgBeauty</td>
   </tr>
   <tr>
      <td>Panel</td>
      <td>Pnl</td>
      <td>pnlTree</td>
   </tr>
   <tr>
      <td>TreeView</td>
      <td>Tv</td>
      <td>tvUnit</td>
   </tr>
   <tr>
      <td>WebComTable</td>
      <td>Wct</td>
      <td>wctBasic</td>
   </tr>
   <tr>
      <td>ImageDateTimeInput</td>
      <td>Dti</td>
      <td>dtiStart</td>
   </tr>
   <tr>
      <td>ComboBox</td>
      <td>Cb</td>
      <td>cbList</td>
   </tr>
   <tr>
      <td>PageBar</td>
      <td>Pb</td>
      <td>pbMaster</td>
   </tr>
   <tr>
      <td>MyImageButton</td>
      <td>Mib</td>
      <td>mibOK</td>
   </tr>
</table>
注意区别组件示例名和组件类型名，在VS中，新建一个Form是新建一个Form类型，类似于：

    public partial class Form1 : Form
    {
     ……
    }

这里的Form1是组件类型名，继承与Form，应遵守命名的基本约定中对类型的约束，采用帕斯卡命名法，如：

    public partial class LoginForm : Form
    {
     ……
    }

当需要实例化它时，则采用匈牙利命名法，如：

    LoginForm lfLogin = new LoginForm();
    lfLogin.Show();

但Form类型绝大多数情况下是只需实例一次的，所以代码可以写成：

    (new LoginForm()).Show();

避开繁杂的匈牙利命名。减少代码中不必要的局部变量命名，也是提高代码质量的方法之一。

## 二、代码注释 ##

### 2.1 代码注释约定 ###

所有的方法和函数都应该以描述这段代码的功能的一段简明注释开始（方法是干什么）。这种描述不应该包括执行过程细节（它是怎么做的），因为这常常是随时间而变的，而且这种描述会导致不必要的注释维护工作，甚至更糟—成为错误的注释。代码本身和必要的嵌入注释将描述实现方法。

当参数的功能不明显且当过程希望参数在一个特定的范围内时，也应描述传递给过程的参数。被过程改变的函数返回值和全局变量，特别是通过引用参数的那些，也必须在每个过程的起始处描述它们。

### 2.2 模块头部注释规范 ###

以一个物理文件为单元的都需要有模块头部注释规范，例如：C#中的.cs文件

用于每个模块开头的说明，主要包括：（粗体字为必需部分，其余为可选部分）

1. **文件名称(File Name)**： 此文件的名称
2. **功能描述(Description)**： 此模块的功能描述与大概流程说明
3. 数据表(Tables)： 所用到的数据表，视图，存储过程的说明，如关系比较复杂，则应说明哪些是可擦写的，哪些表为只读的。
4. **作者(Author)：**
5. **日期(Create Date)**：
6. 参考文档(Reference)(可选)： 该档所对应的分析文档，设计文檔。
7. 引用(Using) (可选)： 开发的系统中引用其它系统的动态链接库文件。
8. 有关﹙不清楚的可以不写﹚，以方便制作安装档。
9. 修改记录(Revision History)（此项不写，我们的修改记录完全交由Git管理）：若档案的所有者改变，则需要有修改人员的名字、修改日期及修改理由。
10. **分割符：***************************** (前后都要)

示例如下：

    //*****************************************************************************
    //
    // 文件名(File Name): WebTool.cs
    // 
    // 描述(Description): 包含类PVBlue.Tool.WebTool的的声明与定义
    //
    // 作者(Author): 宋建鑫，雷薇
    //
    // 日期(Create Date): 2015/09/04
    //
    // 引用(Using): PVBlue.Database.dll
    //
    //*****************************************************************************

    using System.Windows;
    using System.Threading;
    ……

### 2.3 方法注释规范 ###

1. C# 提供一种机制，使程序员可以使用含有XML 文本的特殊注释语法为他们的代码编写文档。在源代码文件中，具有某种格式的注释可用于指导某个工具根据这些注释和它们后面的源代码元素生成XML。具体应用当中，类、接口、属性、方法必须有<Summary>节，另外方法如果有参数及返回值，则必须有`<Param>`及`<Returns>`节。示例如下：   
`/// <summary>`   
`/// …`   
`/// </summary>`   
`/// <param name=””></param>`   
`/// <returns></returns>`   
2. 事件不需要头注解，但包含复杂处理时（如：循环/数据库操作/复杂逻辑等），应分割成单一处理函数，事件再调用函数。
3. 所有的方法必须在其定义前增加方法注释。
4. 方法注释采用 /// 形式自动产生XML标签格式的注释。
5. 修改任何方法，必须要添加修改记录的注释。

XML注释标记与说明：
<table>
   <tr>
      <td>标记</td>
      <td>说明</td>
   </tr>
   <tr>
      <td>c</td>
      <td>提供了一种将说明中的文本标记为代码的方法</td>
   </tr>
   <tr>
      <td>code</td>
      <td>提供了一种将多行指示为代码的方法</td>
   </tr>
   <tr>
      <td>example</td>
      <td>可以指定使用方法或其他库成员的示例。一般情况下，这将涉及到 code标记的使用。</td>
   </tr>
   <tr>
      <td>exception</td>
      <td>对可从当前编译环境中获取的异常的引用。</td>
   </tr>
   <tr>
      <td>include</td>
      <td>得以引用描述源代码中类型和成员的另一文件中的注释。</td>
   </tr>
   <tr>
      <td>list</td>
      <td>用于定义表或定义列表中的标题行。</td>
   </tr>
   <tr>
      <td>para</td>
      <td>用于诸如summary、remarks 或 returns等标记内，使您得以将结构添加到文本中。</td>
   </tr>
   <tr>
      <td>param</td>
      <td>应当用于方法声明的注释中，以描述方法的一个参数。</td>
   </tr>
   <tr>
      <td>paramref</td>
      <td>提供了一种指示词为参数的方法。</td>
   </tr>
   <tr>
      <td>permission</td>
      <td>得以将成员的访问记入文档。</td>
   </tr>
   <tr>
      <td>remarks</td>
      <td>用于添加有关某个类型的信息，从而补充由 summary所指定的信息。</td>
   </tr>
   <tr>
      <td>returns</td>
      <td>应当用于方法声明的注释，以描述返回值。</td>
   </tr>
   <tr>
      <td>see</td>
      <td>得以从文本内指定链接。</td>
   </tr>
   <tr>
      <td>seealso</td>
      <td>对可以通过当前编译环境进行调用的成员或字段的引用。</td>
   </tr>
   <tr>
      <td>summary</td>
      <td>应当用于描述类型或类型成员。</td>
   </tr>
   <tr>
      <td>value</td>
      <td>得以描述属性。</td>
   </tr>
</table>

示例如下：     

    /// <summary>
    /// 使用MD5计算哈希散列值
    /// </summary>
    /// <param name="strSource">需要加密的字符串</param>
    /// <param name="strSaltCode">盐值</param>
    /// <return>加密后的字符串</return>
    public static string EncryptMD5(string strSource, string strSaltCode)
    {
    	//MD5加密服务对象
    	System.Security.Cryptography.MD5CryptoServiceProvider md5 = new System.Security.Cryptography.MD5CryptoServiceProvider();
    
    	byte[] value;
    	byte[] hash;
    	……

### 2.4 代码行注释规范 ###

1. 如果处理某一个功能需要很多行代码实现，并且有很多逻辑结构块，类似此种代码应该在代码开始前添加注释，说明此块代码的处理思路及注意事项等；
2. 注释从新行增加，与代码开始处左对齐；
3. 双斜线与注释之间以空格分开，

示例如下所示：

    public void Dispose()
    {
    	// 如果事务开启过,则释放事务对象
    	if (this.DIbTrans != null)
    		this.DIbTrans.Dispose();

    	// 如果连接已经打开,则关闭连接并释放资源
    	if (this.IDbConn.State == ConnectionState.Open)
    	{
    		this.IDbConn.Close();
    		this.IDbConn.Dispose();
    	}
    }
 
### 2.5 变量注释规范 ###

1. 定义变量时需添加变量注释，用以说明变量的用途。
2. Class级变量应以采用 /// 形式自动产生XML标签格式的注释。
3. 方法级的变量注释可以放在变量声明语句的后面，与前后行变量声明的注释左对齐，注释与代码间以Tab隔开。

代码示例如下：

    class Crawler
    	{
    		/// <summary>
			/// 需要访问的链接地址
			/// </summary>
    		string _link;
    		/// <summary>
    		/// 保存得到的HTML代码的文件名
			/// </summary>
    		string _fileName;
			
    		/// <summary>
			/// 构造函数
			/// </summary>
			/// <param name="link">需要访问的链接地址</param>
			/// <param name="fileName">保存得到的HTML代码的文件名</param>
    		public Crawler(string link, string fileName)
    		{
    			_link = link;
    			_fileName = fileName;
    		}
    
    		/// <summary>
			/// 抓取指定链接的HTML代码，并保存到文件
			/// </summary>
			/// <exception>
			/// WebException:访问网络失败
			/// </exception>
			/// <returns>是否成功抓取并保存</returns>
    		public bool Crawl()
    		{
    			HttpWebRequest request = (HttpWebRequest)HttpWebRequest.Create(_link);//创建一个网络请求对象
    			request.Method = WebRequestMethods.Http.Get;	//设置请求的方法
    			HttpWebResponse response;						//创建一个网络请求回应对象
			……
 
## 三、其它规范 ##

### 3.1 编程风格 ###

#### 3.1.1 变量声明 ####

为了保持更好的阅读习惯，和方便注释，请不要把多个变量声明写在一行中，即一行只声明一个变量。

#### 3.1.2 代码缩进 ####

一致的代码缩进风格，有利于代码的结构层次的表达，使代码更容易阅读和传阅。

1. 代码缩进使用Tab键实现，不要使用空格，为保证在不同机器上使代码缩进保持一致，一般规定C#的Tab键宽度为4个字符；
2. 所有块的{}号分别开一行放置，并嵌套对齐。

#### 3.1.3 空行与空格 ####

1. 空行将逻辑相关的代码段分隔开，以提高可读性。
2. 下列情况应该总是使用两个空行：   
   a) 一个源文件的两个片段(section)之间。   
   b) 类声明和接口声明之间。   
3. 下列情况应该总是使用一个空行：   
   a) 两个方法之间。   
   b) 方法内的局部变量和方法的第一条语句之间。   
   c) 块注释或单行注释之前。   
   d) 一个方法内的两个逻辑段之间，用以提高可读性。   
4. 下列情况应该总是使用空格： 
   a) 空白应该位于参数列表中逗号的后面；   
   b) 所有的二元运算符，除了"."，应该使用空格将之与操作数分开。一元操作符和操作数之间不因该加空格，比如：负号("-")、自增("++")和自减("--")；   
   c) for 语句中的表达式应该被空格分开；   
   d) 强制转型后应该跟一个空格；   
   （注：Visual Studio 会在用户输入行尾分号后，自动对当前所在行进行空格补全，但培养良好的空格习惯将有利于我们在不同的IDE上都写出好看的代码，若看不明白上面的说明，可观察 Visual Studio 是如何补全空格的，争取能做到写出的代码不再需要 Visual Studio 补全空格） 

### 3.2 资源释放 ###

　　所有外部资源都必须显式释放。例如：数据库连接对象、IO对象等。 

    public void Dispose()
    {
    	// 如果事务开启过,则释放事务对象
    	if (this.DIbTrans != null)
    		this.DIbTrans.Dispose();

    	// 如果连接已经打开,则关闭连接并释放资源
    	if (this.IDbConn.State == ConnectionState.Open)
    	{
    		this.IDbConn.Close();
    		this.IDbConn.Dispose();
    	}
    }
 
### 3.3 异常处理 ###

> 待确定异常抛出、处理、重抛方案后再补全

### 3.4 其它 ###

0. 一个方法只完成一个任务。不要把多个任务组合到一个方法中，即使那些任务非常小。
0. 使用C#的特有类型，而不是System命名空间中定义的别名类型。   
   注：C#是没有自己的数据类型的，比如C#虽然有类型int，但是它没有实现它，int 其实就是.Net提供的System.Int32，所以这里的意思是写 `int i;`而不是写`System.Int32 i;`尽管绝大多数情况下它们是等价的。
0. 尽量不要在程序中使用字面常量做参数，用符号常量代替。
0. 不要把字段声明为 public 或 protected，都声明为 private 而使用 public/protected 的属性；   
   注：C#摒弃了“成员变量”一词，而使用“字段”说明，以示与“属性”的区别这意味所有的字段都将是私有的，不再有非私有字段，属性将取代非私有字段。这一点体现了C#相对于C++的先进性，也是因为这一点，私有字段将成为唯一的字段，给其加下划线前缀合乎情理。
0. 不在代码中使用具体的路径和驱动器名。使用相对路径，并使路径可编程。
0. 应用程序启动时作些“自检”并确保所需文件和附件在指定的位置。必要时检查数据库连接。出现任何问题给用户一个友好的提示。
0. 如果需要的配置文件找不到，应用程序需能自己创建使用默认值的一份。
0. 如果在配置文件中发现错误值，应用程序要抛出错误，给出提示消息告诉用户正确值。
0. DataColumn取其列时要用字段名，不要用索引号。
0. 在一个类中，字段定义全部统一放在class的头部、所有方法或属性的前面。
0. 在一个类中，所有的属性全部定义在一个属性块中：
 

 

 

 

 

 

 

 

 

 

 

 

 

 

 
## 一、命名规则 ##

### 1.1 命名的基本约定 ###

1. 要使用可以准确说明变量/字段/类的完整的英文描述符，如firstName。对一些作用显而易见的变量可以采用简单的命名，如在循环里的递增（减）变量就可以被命名为 “i”。
2. 要尽量采用项目所涉及领域的术语。
3. 要采用大小写混合，提高名字的可读性。为区分一个标识符中的多个单词，把标识符中的部分单词的首字母大写。**不采用下划线作分隔字符的写法。**   
有两种适合的书写方法，适应于不同类型的标识符：   
**帕斯卡命名法**：标识符的每一个单词的首字母都大写；   
**骆驼命名法**：除第一个单词之外，标识符的其他单词首字母大写。   
4. 避免使用缩写，如果一定要使用，就谨慎使用。同时，应该保留一个标准缩写的列表，并且在使用时保持一致。   
5. 对常见缩略词，两个字母的缩写要采用统一大小写的方式（示例：ioStream，   getIOStream）；多字母缩写采用首字母大写，其他字母小写的方式（示例：getHtmlTag）；   
6. 避免使用长名字（最好不超过 15 个字母）。   
7. 避免使用相似或者仅在大小写上有区别的名字。  

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
      <td>private string fieldName;</td>
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

1. 按照使用范围来分，我们代码中的变量的基本上有以下几种类型，类的公有变量；类的私有变量（受保护同公有）；方法的参数变量；方法内部使用的局部变量。　　　　这些变量的命名规则基本相同，见标识符大小写对照表。区别如下：   
　　　　a) 类的公有变量按通常的方式命名，无特殊要求；   
　　　　b) 类的私有变量采用两种方式均可：采用加“m”前缀，例如mWorkerName;   
　　　　c) 方法的参数变量采用camalString，例如workerName；   
2. 方法内部的局部变量采用camalString，例如workerName。
3. 不要用_或&作为第一个字母；
4. 尽量要使用短而且具有意义的单词；
5. 单字符的变量名一般只用于生命期非常短暂的变量：i,j,k,m,n一般用于integer；c,d,e 一般用于characters；s用于string
6. 如果变量是集合，则变量名要用复数。例如表格的行数，命名应为：RowsCount；
7. 命名组件要采用匈牙利命名法，所有前缀均应遵循同一个组件名称缩写列表。
 
### 1.3  组件名称缩写列表 ###

匈牙利命名法的基本原则是：变量名=属性+类型+对象描述，这里将其简化为：组件变量名=组件类型缩写+组件描述。描述缩写的基本原则是取组件类名各单词的第一个字母，如果只有一个单词，则去掉其中的元音，留下辅音。缩写全部为小写。下表列举了一些常见组件的类型缩写以及命名示例：
<table>
   <tr>
      <td>组件类型</td>
      <td>缩写</td>
      <td>例子</td>
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
      <td>MyImageButton</td>
      <td>Mib</td>
      <td>mibOK</td>
   </tr>
   <tr>
      <td>WebComm.TreeView</td>
      <td>Tv</td>
      <td>tvUnit</td>
   </tr>
   <tr>
      <td>PageBar</td>
      <td>Pb</td>
      <td>pbMaster</td>
   </tr>
</table>

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 
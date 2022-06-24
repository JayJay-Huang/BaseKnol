●物件導向
>封裝 (Encapsulation)
隱藏某一方法的具體執行步驟，
把過程和資料包起來，
對資料的操作只能通過已定義的介面(Interface)，
封裝的目的，是讓其他人可以使用物件，
但不需要知道物件的內部邏輯。
目的 : 
增加一定的安全性，防止資訊的洩露、破壞。

講到封裝，得提下訪問修飾符了。
public：所有物件都可以訪問；
private：物件本身在物件內部可以訪問；
protected：只有該類物件及其子類物件可以訪問
internal：同一個程式集的物件可以訪問；
protected internal：訪問限於當前程式集或派生自包含類的型別。

>繼承 (Inheritance)
讓一個類別(子類別subclass)
承另一個類別(父類別superclass)的"方法"和"屬性"，
透過繼承可以達到DRY的目的，
也可以適當的切割類別，
又不破壞原先基底類別設計。
可分為以下系列：
單重繼承：表示一個類可以派生自一個基類，C#採用此繼承
多重繼承：多重繼承允許一個類派生自多個類，C#不支援多重繼承，但允許介面的多重繼承
多層繼承：多層繼承允許有更大的層此結構，類B派生自類A，類C派生自類B，其中，類B也稱為中間基類，C#支援它，也很常用。
介面繼承：允許介面多重繼承

>多型 (Polymorphism)
不同型態的物件，定義相同的操作介面，
由於被呼叫者 (Callee) 有著相同的介面，
呼叫者並不用指定特別型別，只需針對介面進行操作。
>多型指在程式設計中存在同名不同方法的存在，
主要通過子類對父類的覆蓋來實現多型，
設計原則之一就是要依賴於抽象，abstract 
而不依賴於具體，
增加靈活性。多型就是為了體現這一原則。

●泛型
(Generic Type)
它可以讓你在定義Class、Method、Interface時
先不用決定型別，到了要實體化的時候再決定其型別。
System.Collections.Generic特別重要。
LINQ就是一個集合的應用方法，當然就用到了大量的Generic Type。
>
    public class Program
    {
        static void Main(string[] args)
        {
            Demo<string,int> demo = new Demo<string,int>("A",1);

            Console.WriteLine(demo.Get() + demo.GetK<string>("KKK"));
            Console.ReadKey();
        }
    }

// 型態也可不一致
    public class Demo<S,I>
    {        
        private S data1;
        private I data2;

        public Demo(S data1, I data2)
        {
            this.data1 = data1;
            this.data2 = data2;
        }

        public S Get()
        {
            return this.data1;
        }

        public K GetK<K>(K k) // 方法泛型
        {
            K data3= k;
            return data3;
        }

    }

●MVC
>Model
資料庫的連線。資料的定義、讀取、驗證、資料的CURD。
>Contorller
流程的控制。
>View
接收顯示資料。

●大量資料(每秒1000筆)同時存取時，你身為系統開發人員該如何設計可正常運作?
>批次處理
>DataReader、SQL合併

●.NET和C#有什麼區別


--------
●中介軟體


●連接資料庫
ADO.NET
Entity Framework

PHP 超文字處理器
ORM (Object Relational Mapping) 物件關係對映


●MVC

>Model
模型
表示業務數據，並提供數據給視圖。
資料庫的連線、資料的定義、資料的讀取、資料的驗證、資料的CURD。
>Contorller
控制器
接受用戶的輸入並調用模型和視圖去完成用戶的需求。
流程的控制。
>View
視圖
是用戶看到並與之交互的界面。
接收顯示資料。

●MVC的完整流程嗎
所有的終端用戶請求被發送到C。
C依賴請求 去選擇加載哪個M，並把M附加到對應的V。
附加了模型數據的最終視圖做為響應發送給終端用戶。

●Entity Framework的開發方式
>Code First : 由資料庫產生模型。
>Model First : 透過Entity Framework的工具設計模型後再建立資料庫。
>Database First : 程式碼定義模型後再建立資料庫。


●架構MVC
https://ithelp.ithome.com.tw/articles/10158776

●架構WebAPI

●Entity SQL 跟 LINQ 跟  Query Builder Mothed

●.NET 5 與 .NET Framework
https://docs.microsoft.com/zh-tw/dotnet/standard/choosing-core-framework-server

●mvc 4的新的功能


●mvc頁面的life cycle

app initialization. 應用初始化。
Routing. 路由。
Instantiate and execute controller. 實例化並執行控制器。
Locate and invoke controller action. 調用控制器動作。
Instantiate and render view. 實例化並渲染視圖。


●mvc對ASP.net的好處在哪裡？

提供非常清晰的成績管理，像ui層，也就是view, 數據層model和管理層controller。

●razor view engine?
這個引擎提供了數據綁定的顯示模板。

@model MvcStore.Models.Customer

@{ViewBag.Title="Get Customers";}
 
<div class="cust">
<h3>
<em>
@Model.CustomerName
</em>
</h3>
</div>

●Mvc中的路徑是幹什麼的?

一個是路徑的那個"字符串"，還有一個是它的"處理函數"。

●Mvc中的actions

主要處理兩部分內容，一個是視圖，另外一個是json數據。
invoke action這個方法來調用。

●屬性路徑？
調用MapHttpAttributeRoutes。 

>Startup.Configure 使用 傳統路由 : 
"{controller=Home}/{action=Index}/{id?}"

>屬性路徑
[Route("customers/{customerId}/orders")]
將動作直接對應至路由範本。

●委託
委託可以把一個方法作為引數代入另一個方法。
委託可以理解為指向一個函式的引用。
事件是一種特殊的委託。

●重寫Override 是進行基類中函式的重寫。為了適應需要。
●過載Overload 是方法的名稱相同。引數或引數型別不同。

●.net中讀寫資料庫需要用到那些類？他們的作用？
DataSet:資料儲存器。
DataCommand:執行語句命令。
DataAdapter:資料的集合，用語填充。

●string str = null 與 string str = “”
string str = null 是不給他分配記憶體空間
而string str = “” 給它分配長度為空字串的記憶體空間。

●
>引用型別 分配在記憶體的堆上 heap

>值類型別 分配在記憶體的棧上 stack

●.NET構架下remoting和webservice兩項技術
WS主要是可利用HTTP，穿透防火牆。
Remoting可以利用TCP/IP，二進位制傳送提高效率。

●foreach遍歷訪問的物件需要
實現 IEnumerable介面
或
宣告 GetEnumerator方法的型別

●GC
>垃圾收集器。會自動進行管理。
要請求GC，可用 : 
System.gc( )
Runtime.getRuntime( ).gc( )

●String s = new String(“xyz”);建立了幾個String Object?
兩個物件 : 一個是“xyx”,一個是指向“xyx”的引用物件s

●Set裡的元素是不能重複的
iterator()方法來區分重複與否。
equals()是判讀兩個Set是否相等。


●限制一個動作的類型為GET或POST?
[HttpGet] [HttpPOST] 屬性控制

SQL
------
●
Select ID FROM table1 Where LastUpdateDate = (Select MAX
(LastUpdateDate)FROM table1)

●取出表A中第31到第40記錄(SQLServer,以自動增長的ID
作為主鍵,注意：ID可能不是連續的。)

>select top 10 * from A
where id not in (select top 30 id from A)

>select top 10 * from A
where id >(select max(id) from (select
top30 id from A )as A)

●新增
INSERT INTO [dbo].[SFTPDownloadFiles]
( 欄位1,欄位2,... )
VALUES ( '值1','值2',... )
GO

●查詢
SELECT TOP (1000) *
FROM [ESTAMP].[dbo].[SystemLog]
ORDER BY [LogOn]DESC

jQuery
------
●ASPX
<%=DateTime.Now%>

●Razor
@DateTime.Now

●
<script type="text/javascript">
$(function ( ) 
  {
    $.動作( ){ }
  }
function( )
{
  
}
)
</script>

●按鈕
<button type="button">Push Me</button>

●輸入框
<form>
請輸入文字：<input type="text" name="欄位名稱">
</form>




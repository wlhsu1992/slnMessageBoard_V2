# slnMessageBoard_V2
===========================================資料夾改動部分=======================================
/App_Start/RouteConfig.cs

/App_Data/dbMessageBoard.mdf

/Controller/MemberControler.cs、MessageController.cs、ReplyController.cs

/Views/Member、Message、Reply、Shared 

sp_member、sp_message、sp_reply 為MSSQL stored procedure create 檔案
===============================================================================================
[第一次改動-針對issue部分修改]
1. 新增Controller集中擺放專案Session

2. 新增/Model/資料庫相關類別物件 使由ADO.NET抓取資料庫內容與類別模型繫結

3. 將專案使用到Conneciotn.Open()的部分全部改由 using()操作

4. 將資料庫連線字串改寫至web.config

5. 去除MSSQL命令中原本包含 會員權限驗證及排序的操作行為，
　 改由C#程序執行，降低資料庫作業量

6. 修改預存程序對資料庫操作的命名

7. 使用 $"" 語法代替 (+) 運算符組成字串

8. 將所有需要會員權限使用的控制器，在一開始加入Session會員驗證，
　 若不屬於會員直接將頁面導向預設主頁
  =================================================================================================
[第二次改動-針對issue部分修改]
1. 新增SessionManager類別，集中擺放專案使用Session，可通過該類別方法存取Session。

2. 新增標準註解格式。

3. 通過繼承AuthorizeAttribute類別及覆寫其方法，新增自定義判斷會員是否為登入狀態的Attribute。

4. 在Model資料夾下新增ModelManager類別，存放原Controller中操作資料庫程序的程式碼。
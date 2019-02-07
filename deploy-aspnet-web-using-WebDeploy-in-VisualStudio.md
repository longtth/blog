---
title: Deploy asp.net website bằng WebDeploy trong Visual Studio 2017
tags: C#,

---

Bên đội dev web bằng PHP (Wordpress) các thứ thì thường dùng FTP (FTPS/SFTP) để deploy web,  [asp.net](http://asp.net/)  web cũng có thể deploy bằng FTP được, tuy nhiên, với truyền thống  _eat your own s*_  của mình, các bạn Microsoft vẫn chế cho Visual Studio 1 phương thức “chính thống” để deploy web đó là  `Web Deploy`, ngoài việc deploy bằng cách “chép file” như các trình deploy trên nền FTP, WebDeploy còn hỗ trợ deploy trực tiếp lên SQL Server trong 1 click, tham khảo  [link này](http://localhost:4000/1)  để biết thêm chi tiết.

Trong bài này mình sẽ hướng dẫn cách deploy cái web đơn giản không có SQL Server trước,

### Nguyên liệu
-   Dev environment:
-   Visual studio 2017
-   Code của 1 cái  [asp.net](http://asp.net/)  website đã chạy được :)
-   Nếu bạn làm việc ở công ty thì cần: Quyền remote, kết nối được qua port 80, 443, và remote (3389) đến server, nếu làm ở web server cá nhân (thường mở full port) thì không cần care.
-   Server:
-   Windows server 2012 R2 / Windows server 2016 (bản WinServer2008 cũng không sao nhưng bây giờ đã là năm 2019 rồi mà :( )

### Các bước thực hiện:

Remote vào server, tạo 1 cái local account, add nó vào group Administrators  
  
vì cái server có lúc thì sẽ cùng domain với PC của bạn, có lúc thì không, cho nên tốt nhất là nên dùng  `local-administrator-account`  cho việc này. Trong ví dụ này mình dùng chính cái account có tên là  `Administrator`  luôn.
Cài đặt các Component để run được web trên server thông qua Server Manager, tham khảo  [ở đây](http://localhost:4000/2)  .  
Hình ảnh:[![Imgur](https://i.imgur.com/EnBJ0Cx.png)](https://i.imgur.com/EnBJ0Cx.png "Imgur")Imgur
Download WebDeployTool  [link](http://localhost:4000/3)  và install vào Server

Bật VisualStudio, right-click vào project  [asp.net](http://asp.net/), chọn Publish, xong chọn  `IIS, FTP, etc`  xong nhấn Create Profile  
  
[Imgur](https://i.imgur.com/IPHY6iT.png)

setting như sau:  

Publish method: Web Deploy  

Server:  [http://1.2.3.4](http://1.2.3.4/)  (IP của server của bạn)  
Site name: Default Web Site (iis tự tạo cho bạn 1 cái site tên  _Default Web Site_  trong  `C:\inetpub\wwwroot`  có thể trực tiếp dùng cái này hoặc tự tạo site khác, tùy nhu cầu).  
User name:  `Administrator`  (như đã tạo lúc nãy)  
Destination URL:  [http://1.2.3.4](http://1.2.3.4/)  
  
[![Imgur](https://i.imgur.com/zjlzMvZ.png)](https://i.imgur.com/zjlzMvZ.png "Imgur")Imgur

save lại và bấm  `Publish`  thôi,  
  
[![Imgur](https://i.imgur.com/L32siIQ.png)](https://i.imgur.com/L32siIQ.png "Imgur")Imgur

Nếu không có vấn đề gì xảy ra, Visual Studio sẽ báo:
```
 2>Web App was published successfully http://10.133.165.186/========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==================== Publish: 1 succeeded, 0 failed, 0 skipped ==========
```

>   
> 
> Written with  [StackEdit](https://stackedit.io/).  
>   
> [1]  [https://docs.microsoft.com/en-us/iis/publish/using-web-deploy/introduction-to-web-deploy](https://docs.microsoft.com/en-us/iis/publish/using-web-deploy/introduction-to-web-deploy)  
>   
> [2][https://jakeydocs.readthedocs.io/en/latest/publishing/iis.html](https://jakeydocs.readthedocs.io/en/latest/publishing/iis.html)  
>   
> [3][https://www.iis.net/downloads/microsoft/web-deploy](https://www.iis.net/downloads/microsoft/web-deploy)


> Written with [StackEdit](https://stackedit.io/).

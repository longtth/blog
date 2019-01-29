---


---

<h1 id="deploy-asp.net-website-bằng-webdeploy-trong-visual-studio-2017">Deploy <a href="http://asp.net">asp.net</a> website bằng WebDeploy trong Visual Studio 2017</h1>
<p>Bên đội dev web bằng PHP (Wordpress) các thứ thì thường dùng FTP (FTPS/SFTP) để deploy web, <a href="http://asp.net">asp.net</a> web cũng có thể deploy bằng FTP được, tuy nhiên, với truyền thống <em>eat your own s*</em> của mình, các bạn Microsoft vẫn chế cho Visual Studio 1 phương thức “chính thống” để deploy web đó là <code>Web Deploy</code>, ngoài việc deploy bằng cách “chép file” như các trình deploy trên nền FTP, WebDeploy còn hỗ trợ deploy trực tiếp lên SQL Server trong 1 click, tham khảo <a href="1">link này</a> để biết thêm chi tiết.</p>
<p>Trong bài này mình sẽ hướng dẫn cách deploy cái web đơn giản không có SQL Server trước,</p>
<h3 id="nguyên-liệu">Nguyên liệu</h3>
<ol>
<li>Dev environment:
<ol>
<li>Visual studio 2017</li>
<li>Code của 1 cái <a href="http://asp.net">asp.net</a> website đã chạy được :)</li>
<li>Nếu bạn làm việc ở công ty thì cần: Quyền remote, kết nối được qua port 80, 443, và remote (3389) đến server, nếu làm ở web server cá nhân (thường mở full port) thì không cần care.</li>
</ol>
</li>
<li>Server:
<ol>
<li>Windows server 2012 R2 / Windows server 2016 (bản WinServer2008 cũng không sao nhưng bây giờ đã là năm 2019 rồi mà :( )</li>
</ol>
</li>
</ol>
<h3 id="các-bước-thực-hiện">Các bước thực hiện:</h3>
<ol>
<li>
<p>Remote vào server, tạo 1 cái local account, add nó vào group Administrators<br>
vì cái server có lúc thì sẽ cùng domain với PC của bạn, có lúc thì không, cho nên tốt nhất là nên dùng <code>local-administrator-account</code> cho việc này. Trong ví dụ này mình dùng chính cái account có tên là <code>Administrator</code> luôn.</p>
</li>
<li>
<p>Cài đặt các Component để run được web trên server thông qua Server Manager, tham khảo <a href="2">ở đây</a>  .<br>
Hình ảnh: <img src="https://i.imgur.com/EnBJ0Cx.png" alt="Imgur"></p>
</li>
<li>
<p>Download WebDeployTool <a href="3">link</a> và install vào Server</p>
</li>
<li>
<p>Bật VisualStudio, right-click vào project <a href="http://asp.net">asp.net</a>, chọn Publish, xong chọn <code>IIS, FTP, etc</code> xong nhấn Create Profile<br>
<a href="https://i.imgur.com/IPHY6iT.png">Imgur</a></p>
</li>
<li>
<p>setting như sau:<br>
Publish method: Web Deploy<br>
Server: <a href="http://1.2.3.4">http://1.2.3.4</a> (IP của server của bạn)<br>
Site name: Default Web Site (iis tự tạo cho bạn 1 cái site tên <em>Default Web Site</em> trong <code>C:\inetpub\wwwroot</code> có thể trực tiếp dùng cái này hoặc tự tạo site khác, tùy nhu cầu).<br>
User name: <code>Administrator</code> (như đã tạo lúc nãy)<br>
Password: ***** :)<br>
Destination URL: <a href="http://1.2.3.4">http://1.2.3.4</a><br>
<img src="https://i.imgur.com/zjlzMvZ.png" alt="Imgur"></p>
</li>
<li>
<p>save lại và bấm <code>Publish</code> thôi,<br>
<img src="https://i.imgur.com/L32siIQ.png" alt="Imgur"></p>
</li>
<li>
<p>Nếu không có vấn đề gì xảy ra, Visual Studio sẽ báo:</p>
</li>
</ol>
<pre><code> 2&gt;Web App was published successfully http://10.133.165.186/
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
========== Publish: 1 succeeded, 0 failed, 0 skipped ==========
</code></pre>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.<br>
[1] <a href="https://docs.microsoft.com/en-us/iis/publish/using-web-deploy/introduction-to-web-deploy">https://docs.microsoft.com/en-us/iis/publish/using-web-deploy/introduction-to-web-deploy</a><br>
[2]<a href="https://jakeydocs.readthedocs.io/en/latest/publishing/iis.html">https://jakeydocs.readthedocs.io/en/latest/publishing/iis.html</a><br>
[3]<a href="https://www.iis.net/downloads/microsoft/web-deploy">https://www.iis.net/downloads/microsoft/web-deploy</a></p>
</blockquote>


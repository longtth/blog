<p>Một trong những điều ức chế của khi làm mấy việc dạng sysadmin trong windows là <code>ssh</code>, đặc biệt khi bạn dùng laptop chạy windows, và manage một đống server chạy linux.<br>
May thay, từ Win 10, đội của anh Bill đã về-với-chính-đạo khi <a href="https://quantrimang.com/cach-cai-dat-openssh-tren-windows-10-145183">hỗ trợ OpenSSH</a><br>
Trong bài này, sẽ tóm tắt lại lịch sử vụ ssh-from-windows-with-luv này của mình.</p>
<ol>
<li>Cài OpenSSH vào windows, chi tiết <a href="https://quantrimang.com/cach-cai-dat-openssh-tren-windows-10-145183">tham khảo link trên</a>, tóm tắt như sau:
<ol>
<li>Download OpenSSH từ <a href="https://github.com/PowerShell/Win32-OpenSSH/releases">github Powershell/Win32-OpenSSH/releases</a><br>
chỗ này có điểm 2 củ chuối, 1 là code của openssh-for-windows thì nằm trong <a href="https://github.com/PowerShell/openssh-portable">https://github.com/PowerShell/openssh-portable</a>, nhưng release và issue của nó thì nằm đây,<br>
2 là trong trang <a href="https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse">docs của Microsoft </a>có 1 đoạn hơi bị nguy hiểm, bảo là nếu không cài bằng powershell theo <a href="1">hướng dẫn chuẩn</a> thì phải làm theo hướng dẫn trong cái github kia, chả hiểu các bạn Microsoft nghĩ gì 😂</li>
<li>Chạy cái file powershell để install vào: <code>powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1</code></li>
</ol>
</li>
<li>Bật <code>cmd</code> lên, <code>ssh -i user@ip</code> như một vị thần</li>
</ol>
<p>[1] <a href="https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse">https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse</a></p>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>


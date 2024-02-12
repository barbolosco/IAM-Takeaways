# 🪶 Apache lounge

Apace is a widely known web server, in particular, the "lounge" version is synonym for stability and integration.\
Apache installation:\




1. download apache lounge for windows from the link: [https://www.apachelounge.com/download/VS17/binaries/httpd-2.4.58-240131-win64-VS17.zip](https://www.apachelounge.com/download/VS17/binaries/httpd-2.4.58-240131-win64-VS17.zip)
2. Ensure C++ Redistributable for Visual Studio is Installed: Make sure you have the relevant C++ Redistributable for Visual Studio installed on your server. If unsure, download and run "vc\_redist\_x64.exe" (for 64-bit) or "vc\_redist\_86.exe" (for 32-bit) from ApacheLounge.
3.  &#x20;**Unzip:**

    Once the download is complete, unzip the downloaded "httpd-2.4.58-win64-VC17.zip" file to a suitable location on your server, e.g., C:\Apache24 or D:\Apache.
4.  &#x20;**Configure Apache:**

    After extracting Apache, configure it by:
5. Updating httpd.conf:
   * Locate and open the "httpd.conf" file in a text editor.
   * Update the ${SRVROOT} variable to match your Apache installation directory (e.g., from "C:/Apache24" to "D:/Apache").
   * If no SRVROOT variable exists, manually update instances of "C:/Apache24" throughout the file.
6. Modify Configuration Settings:
   * Add "ExecCGI" to the "Options" directive.
   * Uncomment and update lines for handling .cgi and .pl files.
   * Add "ScriptInterpreterSource Registry" to the end of the httpd.conf file.
7.  **Start Apache:**

    Open a Command or PowerShell prompt in the "bin" folder where Apache was extracted.
8. Start Apache:
   * In Command Prompt, enter: httpd.exe
   * In PowerShell, enter: & "D:\Apache\bin\httpd.exe"
   * If prompted by Windows Firewall, allow access.
9. Troubleshooting:
   * If Apache fails to start due to port binding issues, check for other services using port 80 (e.g., IIS). Stop/disable conflicting services or adjust port settings.
10. **Check Apache:**

    Keep the command prompt open and navigate to [http://127.0.0.1](http://127.0.0.1/) in a web browser. Confirm Apache is running by verifying the "It works!" message.
11. **Install as a Windows Service:**

    To ensure Apache runs continuously, install it as a Windows service.
12. Open an administrative Command or PowerShell prompt:
    * In Command Prompt: httpd.exe -k install
    * In PowerShell: & "D:\Apache\bin\httpd.exe" -k install
13. Start the service:

    * Type: net start Apache2.4

    You should receive a message confirming successful installation of the Apache2.4 service.\


_**Important notice:**_\
If you are planning to use php on apache you have to install the THREAD SAFE version of PHP


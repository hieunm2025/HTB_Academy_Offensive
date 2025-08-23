# Attacking common application

Nhiều loại ứng dụng web như : CMS (Content Manager Systems), custom web, cổng nội bộ dành cho developer và sysadmin, repo, công cụ giám sát mạng, hệ thống quản lý ticket, wiki, knowledge base, issue tracker, ứng dụng container servlet.

**quan trọng**: cùng một app có thể an toàn ở 1 enviroment, nhưng ở môi trường khác lại dễ bị attack do misconfig hoặc chưa patch. Vì vậy pentester đặc biết chú ý các app này.

**Ứng dụng web là gì?**
Ứng dụng web là ứng dụng tương tác mà người dùng truy cập qua trình duyệt. Mô hình thường thấy là client-server.
- Front-end: giao diện website(cái mà user nhìn thấy) -> chạy ở phía client(browser)
- Back-end: mã nguồn ứng dụng, server, databasr -> chạy ở máy chủ
Bật kể ứng dụng là opensource, thương mại hay cusotm, tất cả đều có thể mắc lỗ hổng nằm trong OWASP Top 10/

Ngoài ra, nhiều ứng dụng có chức năng tích hợp sẵn mà nếu bị lạm dụng cũng có thể dẫn đến RCE.
**Các loại ứng dụng thường gặp**
Web CMS	(Joomla, Drupal, WordPress, DotNetNuke)
Application Servers	(Apache Tomcat, Oracle WebLogic, IBM WebSphere)
SIEM	(Splunk, Trustwave, LogRhythm)
Network Management	(PRTG, ManageEngine OpManager)
IT Management	(Nagios, Puppet, Zabbix, ServiceDesk Plus)
Frameworks	(JBoss, Axis2)
Customer Service	(osTicket, Zendesk)
Search Engines	(Elasticsearch, Apache Solr)
Source Code Mgmt	(JIRA, GitHub, GitLab, Bugzilla)
Dev Tools	(Jenkins, Confluence, phpMyAdmin)
Enterprise Integration	(Oracle Fusion, BizTalk, ActiveMQ)

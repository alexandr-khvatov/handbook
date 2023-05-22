# JSP

Jsp Engine (Jasper) Берет JSP-страницу, которую мы написали (html + директивы) и преобразует в Java класс, расширяющий HttpJspBase (см. рисунок 1),

в свою очередь HttpJspBase extends HttpServlet

```java
 public class HttpJspBase{ // HttpJspBase extends HttpServlet
 @Override 
 public void _jaspService(HttpServletReq req, HttpServletRes res){
 var out=res.getWriter();
 out.write("<html>")
 // ... write to responce
 out.write("</html>")
 }
```

<mark style="color:red;">\_jaspService</mark> вызывается в <mark style="color:blue;">**servlet.service()**</mark>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption><p>Рисунок 1 - Jsp Engine</p></figcaption></figure>

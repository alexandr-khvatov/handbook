---
description: Атрибуты есть не только у Session, но и у Servlet Contex
---

# Attributes Map\<String,Object>

Attributes - Map \<String,Object>:

* Servlet Contex  <mark style="color:purple;">Map \<String, Object></mark> - <mark style="color:orange;">**не используется на практике.**</mark> \
  Одна на все Servlets ( 1 на app ).
* Http Session  <mark style="color:purple;">Map \<String, Object>:</mark> e.g. User который залогинен
  * <mark style="color:red;">@SessionAttribute</mark>
  * <mark style="color:red;">@SessionAttributes</mark>
* Http Request Servlet  <mark style="color:purple;">Map \<String, Object></mark>&#x20;
  * <mark style="color:red;">@RequestAttribute</mark> default     - используются при перенаправлении  и при JSP

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

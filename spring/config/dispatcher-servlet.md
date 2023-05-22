# Dispatcher Servlet

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

```java
            try {
          1.      HandlerExecutionChain handler = getHandler(req); // url path
          2.      HandlerAdapter handlerAdapter = getHandlerAdapter(handler);
                ModelAndView mv = handlerAdapter.handle(req, resp, handler);
          3.     if (mv != null) // if @ResponseBody is used - return response as is
          4.    View view = viewResolvers.resolveView(mv.getViewName());
                view.render(mv.getModel());
            } catch (Exception ex) {
          5.     handlerExceptionResolvers.resolveException(ex);
            }
```

1. Теперь Вместо определения сервлета (он у нас один Dispatcher Servlet) необходимо определить handler ( представляет собой Controller и Interceptors) по URL
2. Далее необходимо определить <mark style="color:purple;">**handlerAdapter**</mark> (он содержит ссылку на <mark style="color:orange;">**WebApplicationContext**</mark>, и включает в себя набор  <mark style="color:orange;">**HandlerMethodArgumentResolver**</mark> (_injecting into a controller method_) и <mark style="color:orange;">**HandlerMethodReturnValueHandler**</mark> _(handles the returned value from the controller method)_)\
   <mark style="color:purple;">**handlerAdapter**</mark> - защищает `DispatcherServlet`от деталей. (Сложная логика вынесена в отдельный класс (<mark style="color:purple;">**handlerAdapter**</mark> ))
3. Если mv равен null то с контроллера возвращаются данные, а не Страницы(JSP). Для этого используется аннотация @ResponseBody, которая возвращает не modelAndView,а данные как есть.
4. viewResolvers - которые по названию jsp-страницы знают где физически она расположена у нас в приложении.\
   Model - позволяет делать страницы динамическими.
5. handlerExceptionResolvers - обработчики ошибок

Interceptor - Аналог Filter, вызываются до / после метода Controller

<div align="center">

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

</div>

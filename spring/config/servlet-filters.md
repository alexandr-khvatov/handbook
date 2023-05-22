# Servlet Filters

```java
@WebFilter("/*") // filter mapping 
public class MyCustomFilter implements Filter {
 public void init (FilterConfig config) throws ServletException {}
 public void doFilter (ServletRequest request, ServletResponse response, 
 FilterChain chain) throws IOException, ServletException {
 chain.doFilter(request, response); // filter chain
 } 
 public void destroy() {} 
 }
```

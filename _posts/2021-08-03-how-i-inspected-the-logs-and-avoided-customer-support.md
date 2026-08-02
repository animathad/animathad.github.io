---
title: "How I inspected the logs and avoided customer support!"
tags: [ecommerce, java, security]
description: "tldr; When customer care didn’t respond, inspecting logs worked! 🤣 Got Milk? I have been trying to reset an order from my basket at…"
original_date: 2021-08-03T16:44:40-07:00
---

### tldr;

When customer care didn’t respond, inspecting logs worked! 🤣

#### Got Milk?

I have been trying to reset an order from my basket at [https://countrydelight.in](https://countrydelight.in/dashboard) Everytime it keeps getting stuck with no response. Reached out to customer service, no response!

After trying many permutations and combinations i.e. Buffalo Milk vs Cow Milk. Give me 1 litre daily and or alternate, … Nothing worked. It always got stuck after I clicked Checkout. I was so frustrated, finally started to inspect the console in my browser.

Well for first they send out the entire stack trace which is nice for me 😄 but I take this as a warning to never let them store any of my cards.

#### The stack trace

```
<!doctype html><html lang="en"><head><title>HTTP Status 500 - Internal Server Error</title><style type="text/css">body {font-family:Tahoma,Arial,sans-serif;} h1, h2, h3, b {color:white;background-color:#525D76;} h1 {font-size:22px;} h2 {font-size:16px;} h3 {font-size:14px;} p {font-size:12px;} a {color:black;} .line {height:1px;background-color:#525D76;border:none;}</style></head><body><h1>HTTP Status 500 - Internal Server Error</h1><hr class="line" /><p><b>Type</b> Exception Report</p><p><b>Message</b> Request processing failed; nested exception is java.lang.NumberFormatException: empty String</p><p><b>Description</b> The server encountered an unexpected condition that prevented it from fulfilling the request.</p><p><b>Exception</b></p><pre>org.springframework.web.util.NestedServletException: Request processing failed; nested exception is java.lang.NumberFormatException: empty String
 org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1014)
 org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:909)
 javax.servlet.http.HttpServlet.service(HttpServlet.java:652)
 org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:883)
 javax.servlet.http.HttpServlet.service(HttpServlet.java:733)
 org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:52)
 org.apache.wicket.protocol.http.WicketFilter.doFilter(WicketFilter.java:370)
 org.springframework.orm.hibernate5.support.OpenSessionInViewFilter.doFilterInternal(OpenSessionInViewFilter.java:156)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:320)
 org.springframework.security.web.access.intercept.FilterSecurityInterceptor.invoke(FilterSecurityInterceptor.java:126)
 org.springframework.security.web.access.intercept.FilterSecurityInterceptor.doFilter(FilterSecurityInterceptor.java:90)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.access.ExceptionTranslationFilter.doFilter(ExceptionTranslationFilter.java:118)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.session.SessionManagementFilter.doFilter(SessionManagementFilter.java:137)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.AnonymousAuthenticationFilter.doFilter(AnonymousAuthenticationFilter.java:111)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.rememberme.RememberMeAuthenticationFilter.doFilter(RememberMeAuthenticationFilter.java:150)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.servletapi.SecurityContextHolderAwareRequestFilter.doFilter(SecurityContextHolderAwareRequestFilter.java:158)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.savedrequest.RequestCacheAwareFilter.doFilter(RequestCacheAwareFilter.java:63)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.www.BasicAuthenticationFilter.doFilterInternal(BasicAuthenticationFilter.java:154)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.ui.DefaultLogoutPageGeneratingFilter.doFilterInternal(DefaultLogoutPageGeneratingFilter.java:52)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.ui.DefaultLoginPageGeneratingFilter.doFilter(DefaultLoginPageGeneratingFilter.java:216)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.AbstractAuthenticationProcessingFilter.doFilter(AbstractAuthenticationProcessingFilter.java:200)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.logout.LogoutFilter.doFilter(LogoutFilter.java:116)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.header.HeaderWriterFilter.doHeadersAfter(HeaderWriterFilter.java:92)
 org.springframework.security.web.header.HeaderWriterFilter.doFilterInternal(HeaderWriterFilter.java:77)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.context.request.async.WebAsyncManagerIntegrationFilter.doFilterInternal(WebAsyncManagerIntegrationFilter.java:56)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.context.SecurityContextPersistenceFilter.doFilter(SecurityContextPersistenceFilter.java:105)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.FilterChainProxy.doFilterInternal(FilterChainProxy.java:215)
 org.springframework.security.web.FilterChainProxy.doFilter(FilterChainProxy.java:178)
 org.springframework.web.filter.DelegatingFilterProxy.invokeDelegate(DelegatingFilterProxy.java:358)
 org.springframework.web.filter.DelegatingFilterProxy.doFilter(DelegatingFilterProxy.java:271)
</pre><p><b>Root Cause</b></p><pre>java.lang.NumberFormatException: empty String
 sun.misc.FloatingDecimal.readJavaFormatString(FloatingDecimal.java:1842)
 sun.misc.FloatingDecimal.parseDouble(FloatingDecimal.java:110)
 java.lang.Double.parseDouble(Double.java:538)
 com.gsitw.deliveryexpress.api.Profile.setProfile(Profile.java:870)
 com.gsitw.deliveryexpress.api.Profile.postNewProfile(Profile.java:197)
 sun.reflect.GeneratedMethodAccessor258.invoke(Unknown Source)
 sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
 java.lang.reflect.Method.invoke(Method.java:498)
 org.springframework.web.method.support.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:190)
 org.springframework.web.method.support.InvocableHandlerMethod.invokeForRequest(InvocableHandlerMethod.java:138)
 org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:106)
 org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:888)
 org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:793)
 org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:87)
 org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1040)
 org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:943)
 org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1006)
 org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:909)
 javax.servlet.http.HttpServlet.service(HttpServlet.java:652)
 org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:883)
 javax.servlet.http.HttpServlet.service(HttpServlet.java:733)
 org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:52)
 org.apache.wicket.protocol.http.WicketFilter.doFilter(WicketFilter.java:370)
 org.springframework.orm.hibernate5.support.OpenSessionInViewFilter.doFilterInternal(OpenSessionInViewFilter.java:156)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:320)
 org.springframework.security.web.access.intercept.FilterSecurityInterceptor.invoke(FilterSecurityInterceptor.java:126)
 org.springframework.security.web.access.intercept.FilterSecurityInterceptor.doFilter(FilterSecurityInterceptor.java:90)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.access.ExceptionTranslationFilter.doFilter(ExceptionTranslationFilter.java:118)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.session.SessionManagementFilter.doFilter(SessionManagementFilter.java:137)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.AnonymousAuthenticationFilter.doFilter(AnonymousAuthenticationFilter.java:111)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.rememberme.RememberMeAuthenticationFilter.doFilter(RememberMeAuthenticationFilter.java:150)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.servletapi.SecurityContextHolderAwareRequestFilter.doFilter(SecurityContextHolderAwareRequestFilter.java:158)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.savedrequest.RequestCacheAwareFilter.doFilter(RequestCacheAwareFilter.java:63)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.www.BasicAuthenticationFilter.doFilterInternal(BasicAuthenticationFilter.java:154)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.ui.DefaultLogoutPageGeneratingFilter.doFilterInternal(DefaultLogoutPageGeneratingFilter.java:52)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.ui.DefaultLoginPageGeneratingFilter.doFilter(DefaultLoginPageGeneratingFilter.java:216)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.AbstractAuthenticationProcessingFilter.doFilter(AbstractAuthenticationProcessingFilter.java:200)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.authentication.logout.LogoutFilter.doFilter(LogoutFilter.java:116)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.header.HeaderWriterFilter.doHeadersAfter(HeaderWriterFilter.java:92)
 org.springframework.security.web.header.HeaderWriterFilter.doFilterInternal(HeaderWriterFilter.java:77)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.context.request.async.WebAsyncManagerIntegrationFilter.doFilterInternal(WebAsyncManagerIntegrationFilter.java:56)
 org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.context.SecurityContextPersistenceFilter.doFilter(SecurityContextPersistenceFilter.java:105)
 org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:334)
 org.springframework.security.web.FilterChainProxy.doFilterInternal(FilterChainProxy.java:215)
 org.springframework.security.web.FilterChainProxy.doFilter(FilterChainProxy.java:178)
 org.springframework.web.filter.DelegatingFilterProxy.invokeDelegate(DelegatingFilterProxy.java:358)
 org.springframework.web.filter.DelegatingFilterProxy.doFilter(DelegatingFilterProxy.java:271)
</pre><p><b>Note</b> The full stack trace of the root cause is available in the server logs.</p><hr class="line" /><h3>Apache Tomcat/8.5.63</h3></body></html>
```

I kept seeing this and wondered why are you getting an exception. First logical thought was maybe there is a zero in one of my quantities. Nope! that was not it.

Luckily for me, they reveal so much, I know they are trying to update their profile whenever we checkout. So went to the profile page, the only number field that was empty was Alternate Mobile Number.

#### The problem

Alternate Mobile Number (which was not mandatory) was being set when you checkout and this was throwing an Exception! 🤦‍♂

Updated it & retried checkout. Voila! worked out.

I don’t have to explain how dangerous it is to expose stack trace like this. The rest, good luck to the investors in the company!

If you are curious you have revealed that:

1. Your backend API uses Java with Spring
2. Tomcat version 8.5.63
3. You have a method like this com.gsitw.deliveryexpress.api.Profile.setProfile(Profile.java:870)
4. You parse Alternate Mobile number as Double

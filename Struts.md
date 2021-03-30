# Struts flow of execution

```
Request(Browser) --> web.xml
                        --> Welcome file list
                        --> ActioServlet
                        --> struts-config.xml
                                      --> Action Mapping
                                              --> Path = 
                                              --> action name
                                              --> session
                                                      --> It goes to action class  execute() method
                                                      
                                                      --> return configured in struts-config.xml
                        
                        
```


web.xml

```
<servlet>
  <servlet-name>action</servlet-name>
  <servlet-class>org.apache.struts.action.ActionServlet</servlet-class>
  <init-param>
      <param-name>config</param-name>
      <param-value>/WEB-INF/struts-config.xml</param-value>
  </init-param>
  <load-on-startup>1</load-on-startup>
</servlet>
  <servlet-mapping>
      <servlet-name>action</servlet-name>
      <url-pattern>*.do</url-pattern>
</servlet-mapping>
```


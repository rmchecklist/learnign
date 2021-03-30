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


### web.xml 

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

1. Upon start of the server, container read the data from web.xml and the check for all servlet configured
2. Since we configured(actionServlet) as above, this loads into memory
3. And then init() method will be called
4. init() method read structs config file from struts-config.xml and loaded into main memory
5. When user type the url 
```
e.g.
 http://localhost:8080/app/submitForm.do
```
  - Since url has *.do, with the suffix of do, url will intercepted and processed by actionservlet 
  ```
  <servlet-mapping>
      <servlet-name>action</servlet-name>
      <url-pattern>*.do</url-pattern>
  </servlet-mapping>
 ```
 6. ActionServlet delegates the request handling to another calss called RequestProcessor by invoking process() method

```
<action-mappings>
    <action path="/submitForm"
        type="com.example.EmpAction"
        name="EmpForm"
        scope="request"
        validate="true"
        input="myform.jsp">
        <forward name="success"
        path="success.jsp"/>
        <forward name="failure" path="failure.jsp" />
    </action>
</action-mappings>
<form-beans>
    <form-bean name="EmpForm" type="com.example.form.LoginForm"/>
</form-beans>
```

7. Request processed looks up the configuration file for the URL pattern/SubmitForm(http://localhost:8080/app/submitForm.do)
8. Mapping action is not found then error message will be displayed to the client. [path="/submitForm"]
9. From Mapping action, request processor verifies the all form-bean configuredd to check any form bean tag name is mapping with that name[<form-beans>]. If no name then throw error message
10. type attribute is nothing but FormBean fully qualified java class
11. If #10 found then instantiate class and put it in appropriate scope[session/request --> <action-mapping>] 
12. Requestprocessor checks for the 'validate' attirbute if it's set to true then call validate() from EmpForm[html form data validation]
13. Requestprocessor instantiates the action class specified in the action mapping[EmpAction] and invoke execute() method

```
public ActionForward execute(ActionMapping mapping,
ActionForm form, HttpServletRequest request,
HttpServletResponse response) throws Exception
{
    //your logic
    return mapping.findForward("success");
}
```
14. Forward the request to jsp(success.jsp)


### Form Bean

 - It is a java bean and it extends ActionForm class

1. Static Forms
      - ActionForm
      - ValidatorForm
      - ValidatorActionForm

  When you using static form, you need to do following things

    1. Create a java class by extending one of the above method
    2. Declare a field same as JSP
    3. get/tet method for all fields
    4. If you want to validate, override the validate() method in the Form Bean class
    5. Reset form fiedls need to override the reset() 

2. Dynamic Forms
    - DynaActionForm
    - DynaValidatorForm
    - DynaValidatorActionForm

  When you are using dynamic form, you need to do the following things
  
   1. Write a field declation inside the struts configuration file(no need to write java class with private field and set/get method)
   2. DynamicForms will reset automatically to default values(no need to override reset method)
   3. Dynamic forms will use validation framwork for the form validations (no need to override the validate method)

## Action Class:

 - It defined the busincess logic
 - Handles the client request and prepare the response
 - it also decides where the response should be forwared
 - These are multithreaded.
 
 
 Type of action class:
 
  - Action
  - DispatchAction
  - LookDispatchAction
  - MapptingDispatchAction
  - IncludeAction
  - ForwardAction
  - SwitchAction
  - LocaleAction
  - DowloadAction
  
  
  Action: 
  
  When you extends Action class, you need to override following four parameters
  
   1. ActionMapping
   2. ActionForm
   3. HttpServletRequest
   4. HttpServletResponse

```
In struts 1.0 Action class has perform() method instead of execute() method ,with the following signature :

Public ActionForward perform(AM,AF,H.S.R,H.S.R)throws ServletException, IOException
{
...
}
```

### Struts validation

[https://www.javawebtutor.com/articles/struts/struts_validation_framework.php](Strus validation)

### Struts tiles

Install tiles by usign the below code struts-config.xml

```
To use struts tiles framework, you have to declare the TilesPlugin in class in the struts configuration file.

<plug-in className="org.apache.struts.tiles.TilesPlugin">
    <set-property property="definitions-config"
        value="/WEB-INF/tiles-definitions.xml" />
    <set-property property="moduleAware" value="true" />
</plug-in>
```
Layout.jsp==> Define the structure of the jsp page in the tiles-defs.xml

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<!DOCTYPE tiles-definitions PUBLIC "-//Apache
Software Foundation//DTD Tiles Configuration 1.1//EN"
"http://jakarta.apache.org/struts/dtds/tiles-config_1_1.dtd">
<tiles-definitions>
    <definition name="layout" page="/Layout.jsp">
        <put name="header" value="/header.jsp" />
        <put name="body" value="/body.jsp">
            <put name="menu" value="/menu.jsp">
                <put name="footer" value="/footer.jsp">
    </definition>
</tiles-definitions>

Layout.jsp

<%@page contentType="text/html" pageEncoding="UTF-8"%>
<%@taglib uri="/WEB-INF/struts-html.tld" prefix="html"%>
<%@taglib uri="/WEB-INF/struts-tiles.tld" prefix="tiles"%>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
   "http://www.w3.org/TR/html4/loose.dtd">
 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>
<tiles:getAsString name="title" ignore="true" />
</title>
</head>
<body>
<table border="1" cellpadding="2" cellspacing="2" align="center">
<tr>
<td height="10%" colspan="2"><tiles:insert attribute="header" />
</td>
</tr>
<tr>
<td width="20%" height="250"><tiles:insert attribute="menu" />
</td>
<td><tiles:insert attribute="body" /></td>
</tr>
<tr>
<td height="15%" colspan="2"><tiles:insert attribute="footer" />
</td>
</tr>
</table>
</body>
</html>


```

tiles-defs.xml contains all tile definitions
    







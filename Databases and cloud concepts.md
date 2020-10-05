# Databases and cloud concepts

### THE WEB

#### 1. The Internet

Internet interconnects computing devices, all these device are **hosts** or **end system**主机和终端

**<u>End system</u>** : connect by **communication link** but not direct, the intermediate is **routers**.

**<u>Hosts</u>**: 		**1.server**: program or machine responds requests

​					 **2.client**:program or machine sent requests



![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564220582740.png)

Internet standard developed by the **Internet Engineering Task Force(IETF)** and their documents are known as **RFCs (requests for comments)** they also define protocols.



<u>**Protocols**</u>: a protocol is an agreement on how to communicate



![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564220946993.png)



<u>**HTTP**</u>: Hyper Text Transfer Protocol 超文本协议

​            4 method **CRUD**：	create, read, update, delete

​		    **create**:   creates a new resource in a server assigned location. 							The create interaction is performed by an **HTTP POST** 							method.

​			**read**：   accesses the current contents of a resource. The 							interaction is performed by an **HTTP GET** method.

​			**update**: creates a new current version for an existing resource 							or creates a new resource if no resource already exists 							for the given id. The update interaction is performed 							by an **HTTP PUT** method.

​			**delete**:  removes an existing resource. The interaction is						   performed by an **HTTP DELETE** operation.



​			HTTP is **line-based(lines end with CR LF)**

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564221974209.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564222009871.png)

**URL**: Uniform Resource Locator(RFC 3986) 统一资源定位器

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564222159073.png)

*https is http with extra security

**Query**： ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564222402818.png)

![ ](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564222441567.png)



#### 2. Developing Web Pages

**Markup**: A markup language is used to annotate a document

**HTML**:  Hypertext Markup Language 

​			  information will be display by using tags e.g.<h1><p>

​			  use them to render the content of the page

**HTML5**: simpler, semantic, more features![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564241683038.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564241746842.png)

 <div>
(<div>)= block level tag with no specific meaning

**How to structure your HTML : **1. Use lower case element names

 														 2. Best to close all HTML elements.

​														  3. closing slash (/) 

​														  4. Best to quote attribute values

​														  5. Always add the **alt** attribute to 															  images

​														  6. always define image width and 															  height

​														  7. <html>  or <body> not omit 

​														  8. both the language and the 															  character encoding should be 															  defined early![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564457199330.png)

​															9. layout need to adapt to different 																devices. Use the <,meta> tag![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564457295701.png)

**Forms**:![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564457523947.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564457563916.png)

<u>Input type:</u>




![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564457637901.png)

The **action** attribute defines the action to be performed
when the form is submitted.

e.g. it sent "/comment/comment.php" So this page will contain a server-side script(服务器端脚本) that handle the form data.

**Two method**: <form method="GET | POST"

​						  GET place the form data in the URL parameters by default

​						  POST sent the data in the HTTP request body(fewer limitation and more secure as the data is not visible in the URL)

**Form validation**: type="number" will not let you type letters

​							    required: browser will not let you submit if the

field is empty

​								custom validation with pattern="regexp"(正则)

**placeholder, auto complete**:![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564458544535.png)

**<botton>**: ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564458590228.png)



#### **CSS - Cascading Style Sheets 层叠样式表**

Use HTML for structure and CSS for styling (includes layout, appearance, some behaviours)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564458732256.png)

three pros of using **External**: all HTML files refer to CSS file

​													 Global change easier

​													 all design in CSS and data in HTML![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564458917958.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564458975118.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564464436919.png)

#### 3. Data Formats & Operations

**UNICODE and Encoding**:  file is sequence of bytes, it mean depends

​																	a  how they are encoded

​																	b  what sort of file type it is 

**ASCII**: American Standard Code for Information Interchange

**UNICODE**: first 128 characters of Unicode (which correspond one-to-one with ASCII) are encoded using a single byte with the same binary value as ASCII, making valid ASCII text valid UTF-8-encoded Unicode as well.

​				 Unicode  is a character set

​							      is a list of characters with unique decimal numbers

​																				e.g. A = 65, B = 66, C = 67

​								  defined 136k characters

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564629702887.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564629743482.png)

**Tables and CSV**:

​			Tables are 2-dimensional data

​			CSV : Comma Separated Value 逗号分隔值

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564629928646.png)

**Stream Processing**：

In a stream, data items arrive one at a time and you only get to see them once each

We can use streams if processing can be done with one pass over the
data or if you only need to access recent data (temporal locality)

We can’t do stream processing if we need to do multiple passes
through a data set or we need random access to items in the data set

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564630102708.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564630119061.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564630136049.png)Map and filter are stateless per-element tasks: these are easy to parallelise
Some reduce operations (sum, min, max) can also be done in parallel

#### 4. Representing Data as Trees: XML and JSON

**Tree Representation**: A tree structure or tree diagram is a way of representing the hierarchical structure of data.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564804966979.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564805028040.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564805042332.png)

**Escape Characters转义字符**:The character that have escape character before has to be interpreted differently with the same character without prefixed escape character.



**XML vs HTML**:		HTML is displaying information

​								   XML is describing information

 								  XML allows a software engineer to create a vocabulary and use it to describe data – it is an extensible language

​								   XML is the most common tool for data manipulation and data transmission and can be used for data storage

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564806750850.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564806775845.png)

**XML Validation**:  XML have separate steps for validation and processing.  

Two validation methods:  DTD(Document Type Definition) and schema

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564807085626.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564807100942.png)

**Schema Validation**: XML schema are another way of describing an XML document structure ... in XML itself.

XSD = XML Schema Definition

Schemas are more powerful than DTDs.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564807376251.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564807824967.png)

**XPath/XQuery**: provide ways to address node(s) in an XML document

also works for non-XML version of HTML and can be very useful in web application

**XPath**:![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564808025236.png)

**XSLT**:  eXtensible Stylesheet Transformation Language 

a way of transforming XML documents into other documents e.g. XML,HTML,PDF

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564808155187.png)

**XML Summary**:XML: tree-based data format
							DTD, XSD/schema: validation
							XPath: query language for XML
							XSLT: transform XML with templates



**JSON**: JavaScript Object Notation, widely used data format for web application

it is text so it can be used to exchange data between a server and a client browser, and can be parsed and generate by most programming languages.

it is easy to read and write for human



**JSON syntax**: is derived from JavaScript object notation syntax

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564808924139.png)

​							Data is in name/value paire

​							Data is separated by commas

​							Curly braces hold objects

​							Square brackets hold arrays

XML has to be parsed with an XML parser. JSON can be
parsed by a standard JavaScript function or in Java by the
Gson library

**Gson**:





**Templating**:

Templates are written in the FreeMarker Template
Language (FTL), which is a simple, specialized language 

A general-purpose programming language (like Java) is
used to prepare the data e.g. issue database queries, do
calculations. Then, Apache FreeMarker displays that
prepared data using templates

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564809239322.png)

### Relational databases

#### 5. Introduction to Databases SystemI

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564978201545.png)

using CSV files to store small amounts of static data is ok but doesn't scale.

Specialised algorithm and data structures are needed for applications which want to store and process a lot of data efficiently 

Special protocols need to be implemented if data is to be manipulated by multiple users concurrently.

If your data has strong integrity constraints such as "money should not disappear" then specialised recovery mechanisms are required in care of faults.

**Databases Systems**

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564979118439.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564979143087.png)

#### Tables

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564985581441.png)

to address data in a table: KEYS

**SUPER KEY**: a combination of fields that uniquely determined a row

which mean after choosing data for the field in the super key, there is no choice over the rest of the data in that row.

e.g. (house, postcode) is the super key for above pictures. Because these two determined the street and town.

**CANDIDATE KEY(KEY)**: a super key that is also minimal

which mean if remove any field from a key it ceases to be a super key

**SQL**:![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564986076551.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564986088050.png)

DROP TABLE lecture : Drop table lecturer row/col

DROP TABLE IF EXIST lecture : Drop when exist![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564986199688.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564986325169.png)

Table constraints are a way of asking your DBMS to guarantee the integrity of your data.

constraints are an opportunity for you to give more information to the DBMS and it will stop you doing stupid

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564986362397.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564986964542.png)

some example of sql![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564987070732.png)

#### 7. Projection and Selection

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565333876166.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565333909819.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565336339673.png)

SQL treats NULL as an absence of data : "don't know"

build in function and operators return when any of their input is NULL.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565336490407.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565336514543.png)

1. always know if your can be NULL
2. if your data cannot be NULL declare the field as NOT NULL
3. if your data can be NULL, consider the IS NULL case in your selections.

#### 8. Product and Join

cartesian product contains all possible combinations.

假设集合A={a, b}，集合B={0, 1, 2}，则两个集合的笛卡尔积为{(a, 0), (a, 1), (a, 2), (b, 0), (b, 1), (b, 2)}。![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565337112832.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565354267611.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565354335997.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565354386653.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565354407341.png)

E-R diagram (entity relationship diagram)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565354558506.png)

#### 9. Aggregation, Nested queries

##### **Aggregation** :

 **group by x** which mean x becomes a key on the output table. for example, if the table was have 10 rows but x only have three value then the table afterward will become 3 rows. the left rows specified by aggregation functions.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565530089820.png)



there may have some limitation e.g. like abc.. can not be avg() but it can be max().

you can also add column like

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565530388456.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565530821080.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565530856778.png)

SQL Aggregate Function

MIN()	MAX()	AVG()	SUM()	COUNT()	COUNT(DISTINCT ..)	COUNT(*)...



When have to filter after **GROUP BY** then use **HAVING**

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565531255744.png)

##### **Nested Queries**:

![ ](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565531344037.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565533378950.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565533431661.png)

#### 10-11.Normalisation

Normalisation can make your table in to good shape.

table in normal form are free from redundancy and dependency which cause anomalies(异常现象) when inserting updating and deleting.

**Functional Dependencies**: Definition: An attribute A ***(functionally) depends on*** a set  of attributes XS just if the value of A is uniquely determined after fixing values for XS. We write the functional dependency as XS → A.

e.g. in a table, let say name is uniquely  name → gender.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565852870264.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565852929026.png)

##### **1NF**: 

A schema is in ***1NF*** if there are no collection-valued attributes (sets, lists etc.). Instead, each cell contains only atomic values and each value is a single element.数据库表的每一列都是不可分割的基本数据项，同一列中不能有多个值，即实体中的某个属性不能有多个值或者不能有重复的属性。如果出现重复的属性，就可能需要定义一个新的实体，新的实体由重复的属性构成，新实体与原实体之间为一对多关系。在第一范式（1NF）中表的每一行只包含一个实例的信息。简而言之，无重复的列

##### **2NF**: 

A schema is in ***2NF*** if it is in 1NF and there are no dependencies XS → A in which: 

​				• A is a non-key attribute, and 

​				• XS is all key attributes, but is not a superkey

第二范式（2NF）要求数据库表中的每个实例或行必须可以被惟一地区分

第二范式（2NF）要求实体的属性完全依赖于主关键字。所谓完全依赖是指不能存在仅依赖主关键字一部分的属性，如果存在，那么这个属性和主关键字的这一部分应该分离出来形成一个新的实体，新实体与原实体之间是一对多的关系

e.g. if course and id define name and grade and attendance

​		but course can define attendence

​		id can define name

​		course and id can define attendance, then that is not 2NF, so it will be need to separated id->name & course->grade and new for id,course,attendance. 

An attribute A is said to be a ***key attribute*** just if it is part of some (candidate) key. Otherwise, A is said to be a ***non-key attribute***.

**transitive functional dependence传递函数依赖**: e.g. postcode->city->region

##### **3NF**:

 A schema is in ***3NF*** if it is in 2NF and there are no non-trivial dependencies XS → A with: 

​				• A is a non-key attribute 

​				• XS contains a non-key attribute, but is not a  superkey

满足第三范式的数据库表应该不存在如下依赖关系： 关键字段 → 非关键字段x → 非关键字段y   

   (学号) → (姓名, 年龄, 所在学院, 学院地点, 学院电话) 

　　 这个数据库是符合2NF的，但是不符合3NF，因为存在如下决定关系： 

　　 (学号) → (所在学院) → (学院地点, 学院电话)   

##### **BCNF**:

A schema is in BCNF if it is in 3NF and there are no non-trivial dependencies XS → A with: 

​				• A is a key attribute 

​				• XS is not a superkey

```
对于BCNF，在主码的任何一个真子集都不能决定于非主属性。关系中U主码，若U中的任何一个真子集X都不能决定于非主属性Y，则该设计规范属性BCNF。例如：在关系R中，U为主码，A属性是主码中的一个属性，若存在A->Y,Y为非主属性，则该关系不属性BCNF。
```

   假设仓库管理关系表为StorehouseManage(仓库ID, 存储物品ID, 管理员ID, 数量)，且有一个管理员只在一个仓库工作；一个仓库可以存储多种物品。这个数据库表中存在如下决定关系： 

　　 (仓库ID, 存储物品ID) →(管理员ID, 数量) 

　　 (管理员ID, 存储物品ID) → (仓库ID, 数量) 

　　 所以，(仓库ID, 存储物品ID)和(管理员ID, 存储物品ID)都是StorehouseManage的候选关键字，表中的唯一非关键字段为数量，它是符合第三范式的。但是，由于存在如下决定关系： 

　　 (仓库ID) → (管理员ID) 

　　 (管理员ID) → (仓库ID) 

　　 即存在关键字段决定关键字段的情况，所以其不符合BCNF范式  

a schema in 3NF is automatically in BCNF unless it contains at least two composite candidate keys that overlap.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565881440041.png)

#### 12. JDBC ：SQL in java （Java数据库连接Java DataBase Connectivity）



![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565939958710.png)

always remember close but if implements java.lang.AutoCloseable then it will auto close whenever the block exist.

All JDBC methods throw the checked exception java.sql.SQLException

`try{`

`// database stuff`

`} catch(SQLexception e){`

`//handle it or bail out`

`}`

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565940076932.png)**Transactions**:

A transaction is a sequence of one or more operations on the database that must be executed as one.

**Atomicity**: Either all the operations in the transaction are completed or none of them are. 

**Consistency**: If the database was consistent before the transaction, it is also consistent afterwards. 

**Isolation**: Transactions execute independently; an incomplete transaction does not influence other transactions. 

**Durability**: Once a transaction is committed, its effects cannot be lost through a later failure.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565941494819.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1565941550277.png)

#### 13.Web security

Rule:

1. All data coming from the client is assumed to be malicious(恶意的) until you have properly validated it

##### **sessions and cookies**:

HTTP is stateless: you sent and get response, it end. send another request, server don't know from same person.

Then, browsers implement cookies to get state, if a response contains COOKIE  header then all further requests to the same server will include this header.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566028915261.png)

TLS = Transport layer secure

**Session tokens**: Use java.util.UUID.randomUUID()

​		• cryptographically random, ≈128 bit entropy

​		• not linked to the username/password

**NEVER**  	include a password or other secret data in cookie.

​				   try and authenticate people by checking if their name appears in 				   the cookie.



**JWT(JSON Web Tokens)**:  suppose to be an alternative to cookies for non-browser clients(app, APIs) 		*easy to get wrong,  consult a security expert



##### **XSS( Cross-Site Scripting跨站脚本攻击)**:

Defence 

1. (HTML)escape any user-generated contend that you display in a html page.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566029605930.png)

​	2. HTTP security headers.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566029683629.png)

if set, only white listed scripts can execute.

##### **CSRF 跨站点请求伪造（Cross-site request forgery）**:

Defence

1. Check the Referrer and Origin HTTP headers.

2. If necessary, use per-request CSRF security tokens
3. Re-authenticate before critical operations
4. For an API, you can add and require custom "X-" headers.

[CSRF 的攻击类型与防御](https://zhuanlan.zhihu.com/p/61827277)

**SOP Same origin policy **:Browsers only allow JavaScript requests to the same origin (protocol, host, port) as the source of the script.

**CORS Cross origin Resource sharing**: if want to do open source then set following header in your responses **Access-Control-Allow-Origin: ***

but instead of *, you van white list particular domains that are allowed.

**TLS transport layer secure**: you should be using TLS if you have a domain name of your own.

**password storage**: base 64 encode and hashing is stupid

theoretical, pick a random salt for each user and store hash.



#### 14.data security

Open Web Application Security Project(OWASP top ten)![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566116021772.png)

##### **SQL injection** 

it can happen if

1. user supplied data contains SQL "escapes" such as quotes.

2. User supplied data gets parsed as SQL.

   always use prepared statements.

   ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566139973052.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566138775852.png)

[sql注入](https://baike.sogou.com/v272986.htm?fromTitle=sql%E6%B3%A8%E5%85%A5)

some symbol need to be have backslash escaping. 

##### **Direct Object Reference**: 

insecure direct object reference can happen if

1. you use direct object references
2. you do not do proper access control

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566140649946.png)

in the example of people account id, you could also add user name so that no one else should know.

**Session key**:![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566141055132.png)

**Business keys**: 

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566141404177.png)

**access control**: 

when a user tried to access an object

1. senitize id (say id only contain letter not number to avoid sql injection)
2. get the subject(currently logged in user)
3. check whether this subject is allowed to access this object
4. log the request, if necessary(log 记录)
5. return the object if it's allowed



#### 15. The Cloud

**Three pros of cloud**:	Faster speed to market

​										  Optimization of resourses

​										  Increased operational efficiency

**Two axes**: 

vertical scaling: 	get a bigger server

​		pro: don't have to change your code

​		con: cost, servers can't grow infinitely

Horizontal scaling:	 get lots of small servers

​		pro: fine-grained approach, incremental cost

​		con: now is a distributed system

Amazon EC2: Elastic Compute Cloud

**AWS  Cloud Infrastructure (Amazon web service)**

**for 1 user**: ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566653094117.png)

**for more then 100 users**:

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566653124911.png)

*failover:失效备缓 为系统备援能力的一种，当系统中其中一项设备失效而无法运作时，另一项设备即可自动接手原失效系统所执行的工作

**For users more then 1000**:![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566653262239.png)

moderate 适中的



**For users to 100,000s 10万**:

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566653609765.png)

ops operation system

CDN是Content distribute network（内容分发网络）的简称，这一技术以往只应用于大型商业性网站。通过使用这种技术，可以将网站上的静态内容（例如.html文件、.jpg图片）和动态内容（例如数据库查询）缓存到CDN提供商位于全球各地的多个服务器上。这样当全世界不同访客访问这个网站的时候，就不再需要通过网站所在服务器读取这些内容，而是可以从就近的CDN缓存服务器上读取，因此内容的读取速度更快，直接影响就是网页的加载速度更快。

Amazon S3: Simple Storage Service



benefits of autoscaling: 

	1. adds and removes servers based on load 根据负载增加减少服务器
 	2. increases elasticity and resilience of service 增加服务的弹性和回弹
 	3. ensure service is cost effective

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566656073282.png)

##### something as a service

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566656114796.png)**IaaS**: rent (virtual) machines directly 

**PaaS**: rent machines + OS + basic SW stack, add your own applications 

**SaaS**: rent software, run in the cloud

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566656204180.png)

##### ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566659491110.png)

##### VMS and Containers

**image镜像**：snapshot of (part of) a computer system that you can continue working with on another machine – or lots of machines.

strategy: configure once, create image, deploy image to many machines.

**deployment script**：program that creates the configuration you want

strategy: write script once, run it on every now machine you need.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566660167773.png)

**package managers**: 

1. Store all software as packages in a repository

2. One-line command to install (usually).
3. Dependency management: 'apt install mariadb' also installs all the required libraries.

e.g.  Java: maven and "artifacts" 

​		Go: go get and "packages" 

​		Ruby: gem and "gems" 

​		Lua: luarocks and "rocks" 

​		Rust: cargo and "crates" 

​		JS/Node: npm and "packages"

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566660491072.png)

**Hypervisor超管理器**:software that emulates(仿真) an entire machine. Now we can have many virtual machines on one physical machine



**Towards Containers**：

1. The java servlet/WAR standard lets you run  different java webapps in the same server.

2. Services such as database connections can be provided for all applications through the server configuration.

##### Docker

A mix of images and deployment scripts:

1. docker provided a repository(存储库) and tools for images - in docker's language, a container is a running instance of an image.
2. a dockerfile is a deploy script that creates an image.

**Container**: lighter than a full virtual machine, keeping most of the advantages of an isolated environment.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566713800715.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566714122631.png)

#### 16. Java EE (enterprise edition)

##### maven

mvn clean 		mvn compile

mvn package			create JAR or WAR archive

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566714880424.png)

using GAE(google app engine) plugin

mvn appengine:run

mvn appengine:deploy



In maven, everything is an artifact and has a  (groupId, artifactId, version) "primary key".

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566715610435.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566715120889.png)

Dependency management with maven:

1. artifacts have(groupID,artifactID,version)
2. artifacts can be hosted in repositories.
3. artifacts can have dependencies, maven resolves these(recursively)
4. everything is downloaded to a cache

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566716317264.png)

**POM 是 Project Object Model 的缩写，即项目对象模型。**

pom.xml 就是 maven 的配置文件，用以描述项目的各种信息。![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566716350155.png)

instance:![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566716503093.png)

##### servlets 小形应用程序

Java application servers and google app engine run applications in WAR files

a JEE server can host multiple applications in different WAR files,with a different context paths.(上下文路径/环境路径)![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566717127130.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566717228595.png)**routing**![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566717257882.png)

**Sessions**![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566717352103.png)

**cookies**

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566717440141.png)

**resources(files)**

usually cannot read file system from a web application, but GAE: place the files you want to read in src/main/resources and load it below

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566717695867.png)

**Servlets**

The server may create a new instance of he servlet class or each request.

so you cannot store any state in servlets.

state goes in:

1. session objects
2. databases/memory cache
3. the application context

##### JSP, JSTL and EL

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566724155303.png)

**Jsp Java server page**	

old version

<% *String name = getName()* %>
**<p>**Hello, <%= *name* %>**</p>**
**<ul>**
<% *for(int j = 0; j < 5; j++) {* %>
**<li>**Item <%= *j* %>**</li>**
<% *}* %>
</ul>

[jsp入门](https://blog.csdn.net/xiu2016/article/details/52834979)

​				<% code %>			run java code

​				<%= variable %>	prints variable value  equal to out.println(...)

​				<%! declaration %>adds class-level code

​				<%@ directive%>	taglib = load library

​												   page = add imports etc.

​													include = include other JSP

Jsp files compile to servlets on first use



**EL expression language**

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566725486349.png)

**JSTL Jsp standard tag library**

```jstl
<%@ taglib 
uri="http://java.sun.com/jsp/jstl/core" 
prefix="c" %>

<c:if test="${name != null}">
<p>Hello, ${name}!</p>
</c:if>
```

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566725794622.png)

JSP function - HTML escaping![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1566725916541.png)

 never use "raw" JSP. JSTL+EL are fine, do the heavy work in real Java code.

JSTL does a lot less then JSP, the point is to easier to read/maintain

##### GAE

PaaS offering

GCE (Google Compute Engine) is the IaaS counterpart[only hardware is yours]

*information about gcloud not record



#### 17 Data in the cloud

##### problem with relational databases

small data: fits in RAM of a commodity machine

medium data: fits on disks of a community machine

big data: does not fit on a community machine![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567044528755.png)

replication: multiple copies of everything

pro: backups, reads are quick everywhere

con: effort to synchronise when writing

sharding(分区): different data in different places

pro: efficiency(particularly when writing) if done well

con: effort to read"far away“ data, less redundancy

could use **NOSQL** (not only sql) 

##### key-value stores

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567044880257.png)

redis, memcached etc. : originally in-memory caches. entire cache lives in memory

redis: append-only file("log") for persistence

memcacheDB: "memcache with persitence"



![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567044973327.png)

popular cache strategies![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567045181351.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567045227304.png)

**Caching with Content Delivery Network (CDN)** 

\+ Good for static & video content, cheap 

\+ URL layer, so no App code refactoring 

\- Not effective for dynamic data 

**Caching Session State (e.g. NoSQL)** 

\+ Removes heavy load from App DB for session data 

\- Requires code refactoring, irrelevant for stateless Apps 

**Caching Layer for DB Queries (e.g. Memcached)** 

\+ Highly effective to speed up read-heavy App DBs 

\- Requires code refactoring, complex for write caching KV Stores

##### Memcache				in Google App Engine

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567045624302.png)

memcache	in-memory, fast but not persisitent

​						values are objects - you need to typecast(类型转换)

​						values must be java.io.serializable, 1mb limit

​						keys are completely up to you

Concurrency(并发)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567045866936.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567046098743.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567046129182.png)



##### document stores

**Relational** DB: too complex (all that joining, hard to modify schema).
**KV** **store**: simple but how do we find all posts with the tag "databases"? Or all posts by David with at least 5 comments?

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567149518622.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567149530764.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567149544051.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567149557081.png)

#### 18. The Datastore

##### datastore entities

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567149775865.png)

Google app engine datastore![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567149789582.png)

everything is an (com.google.appengine.datastore）entity

can "find all entities of a certain kind" but the kind does not define any properties

Keys are immutable (you cannot update them). They can be strings (optional, chosen yourself) or longs (auto-generated).![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567149963528.png)

##### The low level API

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567150235446.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567150258768.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567150279423.png)

##### Datastore Queries

The datastore is not a SQL database.

1. a query can only have one kind(mandatory)
2. filters(combine with and/or clauses)
3. sort orders

the datastore does not do joins, statistics, group etc.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567150558939.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567150599827.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567150993023.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567151014742.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567151132821.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567151146556.png)

##### Index

**Scan and Search**:	**SELECT** * **FROM** Person **WHERE** name = 'David';

**option one**： scan the whole table

cost: O(n) where n = rows

**option two**:	(binary) search in a suitable index

cost: O(log n)

*index = table containing duplicates of some or all of the rows/columns in a table, sorted in a particular order to allow binary search.*

Indexes are managed by the database/ datastore and do not impact normalisation.

##### Datastore Indexes

in all databases, indexable queries are faster.

In GAE datastore, only indexable queries are allowed at all. this is not SQL database

A query can have: 

•	a kind (mandatory*) – automatic index 

•	filters – index required 

•	sort orders – index required.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567237853514.png)

There is an automatic index on every property.

```
if a query contains

1. no filters or sorts, just "fetch all of a kind"
2. one sort, no filters
3. no sort, one simple filter{=,<,>,<=,>=}
4. no sort, one range filter "x<20 AND x>10"

then it takes one binary search plus one step per result to satisfy.


```

```
if a query contains

1. a NOT_EQUAL filter on one property
2. an IN query
3. an OR combination of filters

then it will be execute as multiple queries, e.g. " x<>2" gives two queries for "x<2" and "x>2".
```

```
if a query contains

1. multiple sorts
2. multiple filters on different properties combined with AND
3. an inequality filter and a sort on different properties

it requires a custom index.
```

a query that contain multiple inequality filters on different properties (WHERE a < 2 AND b < 3) is **not allowed** in the datastore.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567238826994.png)

##### Multi-valued Properties

A query on a multivalued property matches if any of the elements match. 

WHERE units = 10010			match the entity

{name：“David”, units: [10010, 20004]}

WHERE num >= 10 				match					{num :[8, 9, 10]}

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567238956745.png)

MVP: multivalued properties![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567239260878.png)

#### 19. Distributed Systems

##### Transactions and ACID

The basic unit of work in a database is the transaction, which can contain one or many statements.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567239459714.png)

A is for Atomicity					a transaction is either performed 												  completely or not at all

C is for Consistency 			  If the database was consistent before a 												  transaction started, then it is also 											      consistent after the transaction.

​					(Read "consistent" as "constraints satisfied".)

I is for Isolation 					  Transactions execute independently – an 												   uncommitted transaction cannot 												   influence other transactions.

D is for Durability					The effects of a committed transaction 													are stored and cannot be lost due to a 													later failure.

##### Scheduling

schedule = order in which operations execute (assuming one at a time, so no true parallelism)
serial schedule = only one transaction is active at any one time (our first example)
serialisable schedule = schedule that has the same effect as some serial schedule

**Serialisable schedules give you atomicity.**
**This prevents many concurrency problems.**

##### Replication

multiple copies of your data (usually in different places).

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567239962234.png)

Split-brain: your network has split into two or more components (often known as a *network partition*). 

Result: your data becomes inconsistent.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567240021087.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567240036148.png)

##### CAP

CAP theorem:	No distributed system can offer all the following three features at once.

Consistency: every node always has the same view of the data. 

*nitpick(吹毛求疵) 	C = linearisability or *atomic consistency*.

Def: each operation (transaction) appears to take  place at a distinct point in time. 	In other words, all schedules are serialisable.可序列化

Availability: every node can always read and write (as long as it's up). 

Partition tolerance: the system continues to function after network partitions.

![è¿éåå¾çæè¿°](https://img-blog.csdn.net/20171031135008394?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhhbmd5dWZlaWppYW5neGk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567240372678.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567240527457.png)Eventual consistency: if everyone stops updating some data, eventually* every server will have the same version of the data. 

(* = usually within less than a second)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567240647734.png)

#### 20. Requests and Tasks

##### Resource limits

**time** **limits**	servlets in GAE have time budge of 1 min

For longer tasks, use Task Queues – the time budget is 10 minutes and a task can split itself into "chunks".

**HTTP Requests Limits**	servlets an tasks can make HTTP requests

A HTTP request has a time budget of 5 seconds by default – you can extend this up to your full 1 or 10 minute budget.
A request can contain at most 10 MB data, a response at most 32 MB

##### HTTP Requests

documentation( this section on urlfetch package)

https://cloud.google.com/appengine/docs/standard/java/javadoc/

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567240898712.png)

disallowTruncate(禁止截断): instead of silently truncating the response at 32 MB, throw a ResponseTooLargeException in this case.

withDeadline: increase the request time budget (seconds) – you cannot exceed the servlet's one.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567241097021.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567241148490.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567241164376.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567241206074.png)

##### Tasks and Task Queues

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567241674074.png)

A task (handler) is ... just another servlet.
Except that it's called by the task scheduler, not the client, and has different limits

A task does *NOT* return a value. It can interact with services such as the datastore though.

A task, like any other servlet, can add more tasks to the queue to process things in chunks.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567241758124.png)

A GAE "push" queue has a fixed bucket size(存储数量) of tokens that replenish(补充) at a constant rate

It takes one token to execute a task. 

By default, the bucket size is 5 and tokens replenish  at 5 per second – so you can execute tasks at a rate of 5 per second.

These parameters are configurable

 

Task queues are asynchronous(异步的) – tasks can get executed concurrently, or in any order, in rare cases even more than once.

One way to be safe is to make your tasks idempotent(幂等性): running a task twice has the same effect as running it once.

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242059011.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242090513.png)

**to create a task**

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242120830.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242151909.png)

**failure**

when a task fails(exception, timeout or non-2XX HTTP return code), by default GAE will put it back in the queue.

This means you have to write your tasks in a way that avoids infinite put-back loops.

1. catch exceptions
2. write an error message somewhere, then return "200 OK" to give up

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242255291.png)Tasks may run on a different machine to the servlet that created them.
This means they cannot share (references to) Java objects in memory.
You can pass serialised java objects to a task, or you can pass ids( maybe identification data) and let the task retreive(检索) the necesssary data itself.

##### Scheduled Tasks

Not actually "tasks" on a queue – GAE just calls these at regular intervals(间隔).

The call is a GET request without parameters.

The call is made with "admin" rights so you can stop clients accessing the servlet directly.![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242609259.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242648102.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242663600.png)

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242679780.png)

 ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1567242877386.png)

以太网




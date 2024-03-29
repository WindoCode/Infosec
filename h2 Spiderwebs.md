# Homework 2


## A) Read and summarize OWASP 2021 (3 examples)


1. [A05:2021-Security Misconfiguration](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/)

What and how Security misconfigurations happen?

Security misconfigurations occur when any part of the application stack lacks appropriate security hardening or when permissions on cloud services are improperly configured. This includes setting secure values for security settings, permissions, and security headers. Misconfigurations can open security vulnerabilities when unnecessary features like ports, services, pages, accounts, or privileges are enabled or installed. Default accounts and their passwords should be disabled or changed to prevent unauthorized access. Security misconfigurations can also result from inadequate error handling that reveals stack traces or overly informative error messages. Additionally, not enabling or securely configuring the latest security features for upgraded systems and using out-of-date or vulnerable software components can leave the application at risk.

How can you prevent security misconfigurations from happening?

- Install only programs you need and use. Remove the programs that are no longer needed. This reduces attack surface and minimizes potential security vulnerabilities stemming from unused or unnecessary software.
- Try to develope enviroments identically, with diffrent credentials used in each enviroment. This consistency reduces the likelihood of unexpected issues or vulnerabilities arising when an application is moved from one environment to another.
- Review and audit the security of your platform: These audits can help identify and rectify any misconfigurations or vulnerabilities that may have been missed during initial setup or due to changes over time.


Example attack: 
Scenario: The application server comes with sample applications not removed from the production server. These sample applications have known security flaws attackers use to compromise the server. Suppose one of these applications is the admin console, and default accounts weren't changed. In that case, the attacker logs in with default passwords and takes over.

2. [A06:2021-Vulnerable and Outdated Components](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/)

How you become vulnerable to this?
- You don't know your current version of the components. If you are not running ie.newest version of linux you are vunerable to older attacks.
- You patch your software/enviroment quartely or in a time-frame instead of ASAP. This opens risk for unnecessary exposure to vulnerabilities.
- You dont scan for vulnerabilites regularly or follow security bulletins for your components that you use.

How you prevent this?

Patch managment! For example:

- Remove unused features you dont use in your enviroment.
- Continuously inventory the versions you are using! Subscribe to email alerts for security vulnerabilities related to components you use.
- Only obtain components from official sources over secure links. Using cracked software updates can be a threat to you and your end users.

3. [A03:2021-Injection](https://owasp.org/Top10/A03_2021-Injection/)

How you become vulnerable to this?
- User-Supplied Data is Not Checked: This means that the information entered by users (like in a form or input field) is not being properly examined or cleaned by the application before it's used. Without checking, it could contain harmful data.

- Dynamic Queries Without Safeguards: Dynamic queries are like custom search requests sent to a database. If these queries aren't carefully made and protected, they could accidentally execute harmful commands.
Think of it like opening a box without knowing what's inside – it might contain something dangerous.
If malicious data is directly combined with commands or queries, it can be used to exploit vulnerabilities. Think of it like someone handing you a puzzle piece that, when added to a picture, reveals something harmful, like a hidden trap.

- Some of the more common injections are SQL, NoSQL, OS command, Object Relational Mapping.

How do you defend against injections?

- Use a Safe API or ORM: Instead of directly putting data into your database commands, use a safer way to interact with your database.
- Check Data on the Server: Before you use data that comes from users, double-check it on your server to make sure it's safe to use.
- Use SQL Controls: In your SQL queries, use controls like "LIMIT" to limit the number of records that can be seen.





### Installing [Webgoat](https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/)

For first step, I installed Java. Opening terminal and using following commangs..

```
$ sudo apt-get update
$ sudo apt-get -y install openjdk-17-jre ufw wget bash-completion```

![Photo](https://i.imgur.com/c5Vb9A0.png)

Next installing Webgoat 8. On terminal I used following commands:

```
$ wget https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/webgoat-server-8.0.0.M26.jar
$ java -jar webgoat-server-8.0.0.M26.jar ```

![Installing process](https://github.com/WindoCode/Infosec/assets/110290723/631d8809-dd9a-406b-aca4-7a013919a42e)

Opened WebGoat in browser and had completed the installation. Registered as user! I was asked to disconnect from internet when using this program. Disconnected this virtual machine from right-bottom corner of VirtualBox.

![image](https://github.com/WindoCode/Infosec/assets/110290723/1b0bbdb1-9848-4ec3-899d-6c9083bee11d)

#### F12. WebGoat: General: Developer tools

Firefox developer tools: CTRL+SHIFT+I to open inspect elements tab.

![image](https://github.com/WindoCode/Infosec/assets/110290723/d87a1206-5dbe-46e4-aa8a-8c70caef1b23)

HTML+CSS

Played with some font-colour: turned it to red. ![image](https://github.com/WindoCode/Infosec/assets/110290723/4aa401f4-6898-4277-b7d1-778b0845e1e1)

Console tab: Tried some basic math and JavaScript!:

![image](https://github.com/WindoCode/Infosec/assets/110290723/383ae95f-d019-46e2-83c6-3ecf5b4262a3)

Simple task asked me to put a JavaScript function to console to give an output (Answer to the question through console):

![image](https://github.com/WindoCode/Infosec/assets/110290723/72878923-bc95-4334-9da2-8a0d06ed1697)

From sources pages: I opened file called main.js.

![image](https://github.com/WindoCode/Infosec/assets/110290723/0c85c718-e802-4cc1-8349-259eea2695b3)

Last quiz asked a number that was inside a HTTP request. I did a search inside the Network tab and found the number!

![image](https://github.com/WindoCode/Infosec/assets/110290723/c6e5a599-03ec-4bef-9923-76cb46922297)




##### C) Updating all programs and security stuff

On desktop, I opened terminal and gave command: 

`$ sudo apt-get update`

This command gives us information what we could update.

![epic](https://i.imgur.com/njfO2Ui.png)


After this we updated every possible program that had and update with command:

`$ sudo apt-get -y dist-upgrade`

![image](https://i.imgur.com/IEvtamo.png)

Rebooted the virtual machine.






###### D) SQLZOO 0 SELECT basics

1. **Modify it to show the population of Germany**


```
SELECT population 
FROM world 
WHERE name = 'Germany'
```

2. **Show the name and the population for 'Sweden', 'Norway' and 'Denmark'.**
```
SELECT name, population 
FROM world 
WHERE name IN ('Sweden', 'Norway', 'Denmark');
```

3. **Which countries are not too small and not too big? BETWEEN allows range checking (range specified is inclusive of boundary values). The example below shows countries with an area of 250,000-300,000 sq. km. Modify it to show the country and the area for countries with an area between 200,000 and 250,000.**

```
SELECT name, area 
FROM world 
WHERE area BETWEEN 200000 AND 250000
```


#### SQLZOO, 2 SELECT from World, from first two subtasks (Did 8 for fun)

1. **Observe the result of running this SQL command to show the name, continent and population of all countries.**

```
SELECT name, continent, population FROM world
```

2. **Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.**
```
SELECT name
FROM world 
WHERE population > 200000000
```

3. **Per capita GDP: Give the name and the per capita GDP for those countries with a population of at least 200 million.**
```
SELECT name, gdp/population  
FROM world 
WHERE population>200000000
```

For this one I had to check a tutorial that was submitted from SQLzoo, [Tutorial](https://www.youtube.com/watch?v=5Md75Wfpocs)

4.
```
SELECT name, population/1000000
FROM world
WHERE continent = 'South America'
```

Placed accidentally continent = 'South America' to "FROM" command. Found solution from youtube-video. [Solution](https://www.youtube.com/watch?v=nw1YyPbnKak&t=660s)

5. **Show the name and population for France, Germany, Italy**


```
SELECT name, population
FROM world
WHERE name='France' OR name='Germany'OR name='Italy'
```
Learned to use IF-syntax (in this case OR) on SQL

6. **Show the countries which have a name that includes the word 'United'**

```
SELECT name
FROM world
WHERE name LIKE '%United%'
```
Googled: "how to query search from sql", found w3schools document and read it. This example learned me from wildcard characters.
[w3schools SQL](https://www.w3schools.com/sql/sql_like.asp)

7. **Two ways to be big: A country is big if it has an area of more than 3 million sq km or it has a population of more than 250 million. Show the countries that are big by area or big by population. Show name, population and area.**

```
SELECT name, population, area
FROM world
WHERE population>250000000 OR area>3000000
```
First the result said: not enough tables. Then googled "sql show value in table" Found w3schools link how to show all tables. Selected population and area tables with country name.[w3](https://www.w3schools.com/sql/sql_select.asp)

8. **Exclusive OR (XOR). Show the countries that are big by area (more than 3 million) or big by population (more than 250 million) but not both. Show name, population and area.**

```
SELECT name, population, area
FROM world
WHERE population>250000000 OR area>3000000 
EXCEPT
SELECT name, population, area
FROM world
WHERE population>250000000 AND area>3000000
```
Got a result with China which should not be on table. Googled 'sql exclude'. After that found a code example, eventually the code worked out! [EDUCBA](https://www.educba.com/sql-exclude/)


###### E) Solve Portswigger Labs: Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

SQL Injection - product category filter

```SELECT * FROM products WHERE category = 'Gifts' AND released = 1```
End goal: display all products both released and unreleased.

Analysis:


At first glance we can see 12 products that you could buy. However, if you define your search to for example to 'Pets', you can see 3 products to related to pets. If you look at the URL, you can see that the category you selected gets populeted in a parameter called "category=Pets".

![image](https://github.com/WindoCode/Infosec/assets/110290723/6e06759b-9519-46d8-abe2-6453dc761222)

In this case the query is something like this.

``` SELECT * FROM products WHERE category = 'Pets' AND released = 1 ```

Lets try a query: SELECT * FROM products WHERE category = ''' AND released = 1

![image](https://github.com/WindoCode/Infosec/assets/110290723/4183f171-2a9f-47c6-b167-63dff25e4d62)

So we get internal service error. I am pretty sure this site is exploitable with SQL injection. We tried a single quote mark, which probably ended in an syntax error on the back end. Now we need to build a SQL injection payload to confirm our suspision. 

Building payload

``` SELECT * FROM products WHERE category = ''--' AND released = 1 ```

I use a comment field to ignore everything after the comment field. In this case all of the products that have been released.

So on backend it would query: ``` SELECT * FROM products WHERE category = ''--' ```

![image](https://github.com/WindoCode/Infosec/assets/110290723/421de5fd-53dc-466a-964b-6c40e7433bf7)

We dont get any error and we wont get any search results because the category field is set to nothing. We can confirm that this site is vunerable to SQL injection. 

How we search the relesed and unreleased products with SQL injection?

``` SELECT * FROM products WHERE category = ''OR 1=1 --' AND released = 1 ```

What this will say is select all rows from the products table where category is nothing or conditional statement where 1=1, which translates to TRUE. So it will show **every** product in the products table.

Result:

![image](https://github.com/WindoCode/Infosec/assets/110290723/5a8e83a1-be4d-4f52-b8f9-4be21e6dd4a9)

Lab is solved! gg ez B)












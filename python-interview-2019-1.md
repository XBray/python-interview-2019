## Python开发工程师笔试题

> 答题要求：将该项目从[地址1](<https://github.com/jackfrued/python-interview-2019>)或[地址2](<https://gitee.com/jackfrued/python-interview-2019>)fork到自己的[github]()或[gitee]()仓库并填写答案，完成之后将自己的仓库（public）地址发给面试官即可，答题时间120分钟。

1. 下面的Python代码会输出什么。

   ```Python
   print([(x, y) for x, y in zip('abcd', (1, 2, 3, 4, 5))])
   print({x: f'item{x ** 2}' for x in range(5) if x % 2})
   print(len({x for x in 'hello world' if x not in 'abcdefg'}))
   ```

   答案：

   ```
   a1 = [('a', 1), ('b', 2), ('c', 3), ('d', 4)]
   a2 = {1: 'item1', 3: 'item9'}
   a3 = 6
   
   ```

2. 下面的Python代码会输出什么。

   ```Python
   from functools import reduce
   
   items = [11, 12, 13, 14] 
   print(reduce(int.__mul__, map(lambda x: x // 2, filter(lambda x: x ** 2 > 150, items))))
   ```

   答案：

   ```
   42
   
   ```

3. 有一个通过网络获取数据的Python函数（可能会因为网络或其他原因出现异常），写一个装饰器让这个函数在出现异常时可以重新执行，但尝试重新执行的次数不得超过指定的最大次数。

   答案：

   ```Python
   def retry(func, max_times):
    def call_func(*args, **kwargs):
        for _ in range(max_times):
            try:
                result = func(*args, **kwargs)
            except:
                continue
            if result:
                break
        else:
            return '网络异常未能获取数据'
        return result

    return call_func
   
   ```

4. 下面的字典中保存了某些公司今日的股票代码及价格，用一句Python代码从中找出价格最高的股票对应的股票代码，用一句Python代码创建股票价格大于100的股票组成的新字典。

   > 说明：美股的股票代码是指英文字母代码，如：AAPL、GOOG。

   ```Python
   prices = {
       'AAPL': 191.88,
       'GOOG': 1186.96,
       'IBM': 149.24,
       'ORCL': 48.44,
       'ACN': 166.89,
       'FB': 208.09,
       'SYMC': 21.29
   }
   ```

   答案：

   ```Python
   max_stock = max(prices, key=lambda x: prices[x])

   {index: value for index, value in prices.items() if value > 100}
   ```

5. 写一个函数，传入的参数是一个列表，如果列表中的三个元素`a`、`b`、`c`相加之和为`0`，就将这个三个元素组成一个三元组，最后该函数返回一个包含了所有这样的三元组的列表。例如：

   > 参数：`[-1, 0, 1, 2, -1, -4]`
   >
   > 返回：`[(-1, 0, 1), (-1, 2, -1)]`

   答案：

   ```Python
   def tuple0(list_in):
       list_out = []
       length = len(list_in)
       for i in range(length - 2):
           for j in range(i+2, length):
               if list_in[i] + list_in[i+1] + list_in[j] == 0:
                   list_out.append((list_in[i], list_in[i+1], list_in[j]))
       return list_out
           

   
   ```

6. 写一个函数，传入的参数是一个列表（列表中的元素可能也是一个列表），返回该列表最大的嵌套深度，例如：

   > 参数：`[1, 2, 3]`
   >
   > 返回：`1`
   >
   > 参数：`[[1], [2, [3]]]`
   >
   > 返回：`3`

   答案：

   ```Python
   def count_face(list_in):
       num = 0
       new_list = list_in
       while new_list:
           num += 1
           temp_list = []
           for item in new_list:
               if isinstance(item, list):
                   temp_list.extend(item)
           new_list = temp_list
               
           

   
   ```

7. 写一个函数，实现将输入的长链接转换成短链接，每个长链接对应的短链接必须是独一无二的且每个长链接只应该对应到一个短链接，假设短链接统一以`http://t.cn/`开头。例如：给定一个长链接：，会返回形如：的短链接。

   > 参数：`http://jackfrued.xyz/api/users/10001`
   >
   > 返回：`http://t.cn/E6MUth1`

   答案：

   ```Python
   
   ```

8. 用5个线程，将1~100的整数累加到一个初始值为0的变量上，每次累加时将线程ID和本次累加后的结果打印出来。

    答案：

    ```Python
    
    ```

9. 请阐述Python是如何进行内存管理的。

    答案：

    ```
    python中变量名
    
    ```

10. 在MySQL数据库中有名为`tb_result`的表如下所示，请写出能查询出如下所示结果的SQL。

    `tb_result`表：

    | rq         | shengfu |
    | ---------- | ------- |
    | 2017-04-09 | 胜      |
    | 2017-04-09 | 胜      |
    | 2017-04-09 | 负      |
    | 2017-04-09 | 负      |
    | 2017-04-10 | 胜      |
    | 2017-04-10 | 负      |
    | 2017-04-10 | 负      |

    查询结果：

    | rq         | 胜   | 负   |
    | ---------- | ---- | ---- |
    | 2017-04-09 | 2    | 2    |
    | 2017-04-10 | 1    | 2    |

    答案：

    ```SQL
    select rq, count(shengfu)
    from tb_result
    group by rq, shengfu;
    
    ```

11. 列举出你知道的HTTP请求头选项并说明其作用。

     答案：

     ```
     
     ```

12. 阐述Web应用中的Cookie和Session到底有什么区别和联系。

    答案：

    ```
    Cookie存储在客户端,通常记录一个令牌, Session存储在服务端,通常用来存贮详细的数据
    如在django中, 服务器将每个用户的身份具体信息存储在session中,并将对应的session_id
    返回给浏览器的cookie,如此每次浏览器只要带上cookie,服务器就可以确认用户的身份
    
    ```

13. 请阐述访问一个用Django或Flask开发的Web应用，从用户在浏览器中输入网址回车到浏览器收到Web页面的整个过程中，到底发生了哪些事情，越详细越好。

    答案：

    ```
    django中,服务器收到用户输入的网址后,比对系统功能url,找到对应的view,在实行view前,依次执行预设的中间件request函数
    然后执行对应的view函数,而后再次执行中间件对应的response的函数, 然后对对应的templates进行渲染,返回到浏览器
    
    ```

14. 请阐述HTTPS的工作原理，并说明该协议与HTTP之间的区别。

    答案：

    ```
    HTTPS是安全套接字超文本传输协议,利用证书对数据进行加密传输
    
    ```

15. 简述你认为新浪微博是如何让订阅者在第一时间获得博主发布的消息。

    答案：

    ```
    遍历博主的订阅者, 依次推送博主的消息
    
    ```

16. 简述如何检查数据库是不是系统的性能瓶颈以及你在工作中是如何优化数据库操作性能的。

    答案：

    ```
    对于mysql数据库中经常查询的字段添加索引,
    利用django中debugtoolbar工具条,查看实际的sql语句,优化ORM模型中的查询语句,避免不必要的查询以及n+1的查询问题
    
    ```

17. 在Linux系统中，假设Nginx的访问日志位于`/var/log/nginx/access.log`，该文件的每一行代表一条访问记录，每一行都由若干列（以制表键分隔）构成，其中第1列记录了访问者的IP地址。请用一条命令找出最近的100000次访问中，访问频率最高的IP地址及访问次数。

    答案：

    ```Shell
    
    ```

18. 请阐述跨站脚本攻击（XSS）、跨站身份伪造（CSRF）和SQL注射攻击的原理及防范措施。

    答案：

    ```
    
    ```

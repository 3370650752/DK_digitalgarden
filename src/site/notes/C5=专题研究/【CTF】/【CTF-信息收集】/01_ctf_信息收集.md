---
{"dg-publish":true,"permalink":"/c5/ctf/ctf/01-ctf/","dgPassFrontmatter":true}
---


#CTF-信息收集

# web01:按F12从网页源代码查看信息

# web02:F12无法查看源代码
- 使用ctrl U
- 在地址栏前输入 `view-source:`，例如 `view-source:https://example.com`，然后按回车
- 使用 `curl` 或 `wget` 下载网页源代码，例如 `curl https://example.com`
- 在网页空白处右键点击，选择“查看页面源代码”或“查看源代码”（不同浏览器可能表述不同）
# web03:F12从网络抓包中查看头文件
![Pasted image 20250316101219.png](/img/user/PNG/Pasted%20image%2020250316101219.png)

# web04: 访问robots.txt协议页面拿到被屏蔽的网址

# web05:下载网页php源码查看
![Pasted image 20250316101752.png](/img/user/PNG/Pasted%20image%2020250316101752.png)
# web06:下载网页源码包，访问敏感文件
![Pasted image 20250316102245.png](/img/user/PNG/Pasted%20image%2020250316102245.png)
![Pasted image 20250316102308.png](/img/user/PNG/Pasted%20image%2020250316102308.png)

# web07:版本控制，访问.git/文件查看版本信息
因为.git在linux中为隐藏文件，有些人没注意会部署到网站上面去，造成敏感信息泄露![Pasted image 20250316102602.png](/img/user/PNG/Pasted%20image%2020250316102602.png)

# web08: 版本控制，访问.svn文件查看版本信息

# web09:非正常退出产生的VIM交换文件，访问index.php.swp拿到敏感信息

 swp为交换文件，是vim非正常退出残留的副本
![Pasted image 20250316104431.png](/img/user/PNG/Pasted%20image%2020250316104431.png)

# web10: 查看cookie获取敏感信息

# web11:域名解析隐藏信息
通过域名解析网站实现

# web12:通过网页公开信息获取admin用户密码
网页输入admin进行用户登陆

# web13：查看网页技术文档查看敏感信息

# web14: 源码泄露编译器信息
查看源码，查看编辑器，ctrl+f搜索editor，发现一个路径，访问该路径，是一个编辑器。访问文件上传

# web15:公开信息比如邮箱可能会造成信息泄露
访问admin/，网页上有邮箱，尝试密码为邮箱，失败，忘记密码，修改密码，从邮箱推断密保答案，查看qq，发现是西安，成功修改密码

# web16: 测试探针的信息泄露
php默认探针，tz.php![Pasted image 20250316110519.png](/img/user/PNG/Pasted%20image%2020250316110519.png)
在里面查看phpinfo，然后往下划到环境变量中，即可拿到flag

# web17:通过重重缓存，查找真实ip
可以先用cmd，然后ping + 域名，拿到一层IP地址，如果不同方式ping出来ip不同，说明使用了CDN，
搜索CDN绕过，然后可以尝试能不能复原原地址，这里失败
但是可以使用ping www +域名，因为加了www和不加解析效果不一样

# web19:密钥放前端，查看源码获取
![Pasted image 20250316111529.png](/img/user/PNG/Pasted%20image%2020250316111529.png)
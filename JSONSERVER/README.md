//区分大小写

//获取所有用户信息
http://localhost:3000/users

//获取id为1的用户信息
http://localhost:3000/users/1

//获取公司companies信息
http://localhost:3000/companies

//获取公司companies为1的信息
http://localhost:3000/companies/1

//获取到隶属于某个公司为1的用户
http://localhost:3000/companies/1/users

//获取名字为apple的公司
http://localhost:3000/companies?name=Apple

//获取多个名字获取对应公司
http://localhost:3000/companies?name=Apple&name=Goole

//获取第一页限制展示2个
http://localhost:3000/companies?_page=1&_limit=2

//根据名字降序排序
http://localhost:3000/companies?_sort=name&_order=desc

//获取年龄30及以上的
http://localhost:3000/users?age_gte=30

//获取年龄30-40之间
http://localhost:3000/users?age_gte=30&age_lte=40

//搜索用户信息
http://localhost:3000/users?q=Herry
# DjangoNite
Django笔记


    # 捕获url参数：
    #     1) 位置参数 -- re_path('^parameter(\d+)', users_views.url_par),
    #     2) 关键字参数 -- 视图中参数名必须和正则表达式组名一致
    #           re_path('^parameter(?P<cnt>\d+)', users_views.url_par),

    # 视图中的 request 就是HttpRequest类型的对象
    # request中包含浏览器的请求信息
    #   request中属性信息：
    #       path -- 表示请求页面的完整路径，不包含域名和参数部分
    #           例：127.0.0.1:8000/index?name=jin&password=123 对应path属性为 /index
    #       method -- 表示请求使用的方法
    #       encoding -- 表示提交的数据的编码方式
    #       GET & POST -- QueryDict类型的对象
    #       FILES -- 类似于字典的对象，包含所有的上传文件
    #       COOKIES -- 标准的python字典，包含所有的cookie，键和值都是字符串
    #       session -- 既可读又可写的类似于字典的对象，表示当前会话。需要Django启用会话支持才可用。

    # 注意：ajax请求在后台，不要在ajax中返回页面或者重定向

    # cookie是有过期时间的，若不指定，默认关闭浏览之后cookie就会过期
    # 设置cookie需要一个HttpResponse类对象或者他的子类对象 -- HttpResponseRedirect、JsonResponse、redirect等等
    #   response = HttpResponse("设置cookie")
    #   response.set_cookie('num', 666, max_age=14*24*3600)  # cookie过期时间为两周
    #   或者 response.set_cookie('num', 666, expires=datetime.now() + timedelta(days=14))

    # session 和 cookie 的最大区别：session保存在服务器端
    # session 特点：
    # 1) session 也是以键值对的形式存储的
    # 2) 依赖于 cookie。唯一标识码sessionid 保存在cookie中
    # 3) session 也有过期时间，如果不指定，默认两周就会过期

    # 设置session -- request.session['username']='smart'
    # 获取session -- request.session['password']=666

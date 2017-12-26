# learn
1.express 路由 
Express利用HTTP动作提供了有意义并富有表现力的URL映射API，例如我们可能想让用户帐号的URL看起来像“/user/12”的样子，下面的例子就能实现这样的路由，其中与占位标识符（本例为:id）相关的值可以被req.params获取到。
	
app.get('/user/:id', function(req, res){
    res.send('user ' + req.params.id);
});

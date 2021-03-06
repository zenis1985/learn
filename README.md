# express 
1. 路由 
Express利用HTTP动作提供了有意义并富有表现力的URL映射API，例如我们可能想让用户帐号的URL看起来像“/user/12”的样子，下面的例子就能实现这样的路由，其中与占位标识符（本例为:id）相关的值可以被req.params获取到。
	
```
app.get('/user/:id', function(req, res){
    res.send('user ' + req.params.id);
});
```

2. 路由控制 next
一 个应用中可以定义多个路由，我们可以控制以令其转向下一个路由，Express提供了第三个参数即next()函数。当一个模式不被匹配时，控制将被转回 Connect（Express基于Connect模块），同时中间件会继续按照它们在use()中增加的顺序来执行。当多个定义的路由都可能匹配同一个 URL时也是如此，除非某个路由并不调用next()且已将响应输出到客户端，否则它们也将按顺序执行。

	
```
app.get('/users/:id?', function(req, res, next){
    var id = req.params.id;
    if (id) {
        // 一回注：如果在这里就将响应内容输出给客户端，那么后续的URL映射将不会被调用
    } else {
        next(); // 将控制转向下一个符合URL的路由
    }
});
 
app.get('/users', function(req, res){
    // do something else
});
```
3. 给path 传参数
// Add parameters to the path
// --------------------------
// Express also lets us define variables in the path.  These variables
// will be stored by Express in the `httpRequest.params` object.
// We can then use those variables to construct a response.
// Open a web browser to [http://localhost:4000/steam/hello/Rachel]
// (http://localhost:4000/steam/hello/Rachel).
// 
// Try changing "Rachel" in the URL in the browser.
// 
// ```js

```
app.get('/hello/:name', function(req, res) {
    var name = req.params.name;
    res.send('Hello, ' + name + '!');
});

4.console.time  console.timeEnd 中间的脚本运行时间

5.val = Math.floor(Math.random()*20+1); 1-20随机数。

6.

Getting Started
In order to use the Steam Web API, you have to request a key 
here: https://steamcommunity.com/dev/apikey. 
This key acts as your secret identifier when making requests to the API, s
o don't lose or share it.
Requests contain the following elements

Base URL
    Usually https://api.steampowered.com but there's no guarantee that it won't change in the future.
Interface Name
    Indicates which method group (interface) you want to use. 
    Methods are usually grouped by similarities, but that doesn't seem to be a hard and fast rule.
Method Name
    Indicates which method within the interface you want to use.
Method Version
    Indicates which version of the method you want to use. 
    Valve will occasionally (almost never) update the API and roll the version number on the method. 
    This allows applications to continue working with older versions while 
    new applications can take advantage of the new versions
Parameters
    sometimes optional A one to many list of parameters to be passed to the selected method. 
    Parameters are delimited by the & character.

Request URL format
https://{base_url}/{interface}/{method}/{version}?{parameters}
Sample request URL
http://api.steampowered.com/ISteamWebAPIUtil/GetSupportedAPIList/v1/
Sample request URL with parameters
http://api.steampowered.com/ISteamWebAPIUtil/GetSupportedAPIList/v1/?key=1234567890&steamid=000123000456 

7. dota2 稀有度中文请求
https://api.steampowered.com/IEconDOTA2_205790/GetRarities/v1?key=E4CB2BA4075C279BF67CCB0484126A1A&language=zh
8. 游戏api appid
http://api.steampowered.com/ISteamApps/GetAppList/v2 
"appid": 578080,
"name": "PLAYERUNKNOWN'S BATTLEGROUNDS"
9. getscheme for items
https://wiki.teamfortress.com/wiki/WebAPI/GetSchema
10.csgo 物品数据
https://github.com/Step7750/CSGOFloat

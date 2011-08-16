---
title: coffeescript을 node.js/express에서 사용하기 
layout: post
---

# coffeescript을 node.js/express에서 사용하기 

[Coffeescript][coffeescript]는 javascript으로 컴파일되는 언어입니다. 하나의 언어입니다만, 저는 처음 봤을때 [Javascript: the good part][javascript_the_good_part]가 떠오르더군요. 
무엇보다도, Python처럼 간결한 문법을 사용할수 있어서 매력적이더군요. 

[node.js][nodejs]에서 [express][express]을 사용할때, Javascript대신에  [Coffeescript][coffeescript]을 사용하는 방법에는 여러가지 방법이 있을 수 있더군요. 
[Coffeescript][coffeescript]는 [node.js][nodejs]을 사용해서 동작하기 때문에, 간단하게 생각하면,다음과 같이 사용할수 있습니다. 

{% highlight javascript %}
// in app.coffee
app = require('express').createServer()
app.get '/',(req,res) ->
    res.send 'hello world'
app.listen 3000

// in server.js
require("coffee-script")
require('./app.coffee')
{% endhighlight %}

더 간단하게는,

{% highlight bash %}
coffee app.coffee
{% endhighlight %}
즉, [coffeescript][coffeescript]의 coffee으로 직접 실행해도 됩니다. 

[coffeescript]: http://jashkenas.github.com/coffee-script/
[javascript_the_good_part]: http://oreilly.com/catalog/9780596517748
[nodejs]: http://nodejs.org/
[express]: http://expressjs.com/
[brunch]: http://brunchwithcoffee.com/
[brunch_cakefile]: https://github.com/brunch/brunch/blob/master/Cakefile
[express_coffee_sample]: https://bitbucket.org/anarcher/express-coffee-sample
[express_guide_configure]: http://expressjs.com/guide.html#configuration


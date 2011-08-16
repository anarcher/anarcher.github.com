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

하지만, 매 요청마다 coffeescript을 javascript으로 컴파일하는 건 불필요한 작업이라는 생각이 들더군요. __간단하게 *.coffee 을 *.js으로 컴파일 하고, 개발 모드일때는 coffee app.coffee처럼 사용하다가, 서비스할때는 컴파일 된 javascript으로 사용하는 것이 적절하지 않을까 싶습니다.__

[Brunch with coffee][brunch]의 [Cakefile][brunch_cakefile]을 가지고 간단하게 coffeescript을 javascript으로 컴파일해서 [사용][express_coffee_sample]해보려고 하고 있습니다. 

간단하게 [소스][express_coffee_sample]을 보면, 

{% highlight bash %}

-rw-r--r--   1 anarcher  staff  2272  8 16 16:57 Cakefile
drwxr-xr-x   4 anarcher  staff   136  8 16 16:58 build
-rw-r--r--   1 anarcher  staff   203  8 16 16:58 package.json
-rw-r--r--   1 anarcher  staff   259  8 16 16:58 server.js
drwxr-xr-x   4 anarcher  staff   136  8 16 16:58 src

vacuum:express-coffee-sample anarcher$ cake

cake setup                # Install development dependencies
cake build                # Compile CoffeeScript to JavaScript
cake clean                # Clean up build/
cake watch                # Continously compile CoffeeScript to JavaScript

{% endhighlight %}

cake build을 해서 src에 있는 coffee을 build의 js으로 컴파일합니다. 

express의 [configure][express_guide_configure]으로 development/production mode을 구분하여, production mode일때는 build에 있는 js을 사용하고, development mode일 경우에는 src의 coffee을 사용하면 되지 않을까 합니다. 

이런 build 과정이 번거롭긴 합니다만, front-end에서도 resource(js,css,image)에 대한 minify,compression,versioning 처리를 해야 해서, 이런 front-end에서 필요한 과정과 함께 처리하면 어떨까 합니다. 

ps. 제가 node.js을 가지고 논지 며칠 안되어서, 아는 것이 좀 부족해서 많은 부분이 없군요. :-) 

[coffeescript]: http://jashkenas.github.com/coffee-script/
[javascript_the_good_part]: http://oreilly.com/catalog/9780596517748
[nodejs]: http://nodejs.org/
[express]: http://expressjs.com/
[brunch]: http://brunchwithcoffee.com/
[brunch_cakefile]: https://github.com/brunch/brunch/blob/master/Cakefile
[express_coffee_sample]: https://bitbucket.org/anarcher/express-coffee-sample
[express_guide_configure]: http://expressjs.com/guide.html#configuration


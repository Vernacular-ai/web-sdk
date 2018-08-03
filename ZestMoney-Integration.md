SDK Integration:
================

Follow these steps to integrate the Web SDK:

**1-** Define the following `div` inside body of the html file:

`<div class="vernacular-web-sdk"></div>`

**2-** Include following code to load SDK and create instance of that.

```
// use the given code snippet
<script type="text/javascript" async src="https://cdn.vernacular.ai/vernacular.sdk.fdf8d31a.js" onload="vernacularSDKInit()"></script>

<script type="text/javascript">
  function vernacularSDKInit() {
    window.vernacular.api.init({
      accessToken: '7c98a474-7162-11e8-9650-0242ac110002',
    })
  }
</script>
```

> Note: We can pass other cofigurable properties in `api.init` method, check SDK [doc](https://gist.github.com/MayankShukla5031/ea4a7278edecc0c84d49fdbce16b956c) for details.

**3-** Include this code to hide the Olark chat bot:

**a-** Call this method in olark code snippet (check the example section for sample)
```
olark('api.box.hide');
```

##### Example:

```
<script type="text/javascript" async> ;(function(o,l,a,r,k,y){if(o.olark)return; r="script";y=l.createElement(r);r=l.getElementsByTagName(r)[0]; y.async=1;y.src="//"+a;r.parentNode.insertBefore(y,r); y=o.olark=function(){k.s.push(arguments);k.t.push(+new Date)}; y.extend=function(i,j){y("extend",i,j)}; y.identify=function(i){y("identify",k.i=i)}; y.configure=function(i,j){y("configure",i,j);k.c[i]=j}; k=y._={s:[],t:[+new Date],c:{},l:a}; })(window,document,"static.olark.com/jsclient/loader.js");

  olark.identify('XXXX-XXX-XX-XXXX');

  olark('api.box.hide');      // <======= here

</script>
```

**b-** Include this CSS in the HTML file:

```
<style type="text/css">
  #olark-wrapper {
    display: none !important;
  }
</style>
```

### Few Important points:

1- Define Vernacular script first before Olark script to avoid issues, becasue we are capturing the Olark events.

2- Make sure to hide the Olark chatbot.

3- All the pages where you want to integrate the Vernacular SDK, on the those pages integrate Olark SDK also, because we will send all the messages and notication to their system after bot pause.

4- We have added a new command **(!unpause)** listener at our end to unpause the bot from Olark dashboard.

----------------------------------------

Kindly refer the Web SDK [doc](https://gist.github.com/MayankShukla5031/ea4a7278edecc0c84d49fdbce16b956c) for all other properties and methods.

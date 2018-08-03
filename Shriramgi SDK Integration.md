SDK Integration
===============

Follow these steps to integrate the Web SDK.

**1-** Define the following `div` inside body of the html file: 

`<div class="vernacular-web-sdk"></div>`

**2-** Include following code to load SDK and create instance of that.

```
<script type='text/javascript'>
  $(document).ready(function () {
    $.getScript('https://cdn.vernacular.ai/vernacular.sdk.e863894e.js', function() {
      window.vernacular.api.init({ 
        accessToken: '774f3b52-bf3a-4560-9714-1dececd483b7',
        themeColor: '#FBBD08',
        botName: 'ShriramGI Help Desk',
        botImage: 'Full Image Url',
      });
    });
  });
</script>
```

Kindly refer the Web SDK [doc](https://gist.github.com/MayankShukla5031/ea4a7278edecc0c84d49fdbce16b956c) for all other properties and methods.

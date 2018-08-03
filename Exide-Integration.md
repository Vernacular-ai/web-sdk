SDK Integration:
================

Follow these steps to integrate the Web SDK:

**1-** Define the following `div` inside body of the html file:

`<div class="vernacular-web-sdk"></div>`

**2-** Include following code to load SDK and create instance of that.

```
// use the given code snippet

<script type='text/javascript'>
  $(document).ready(function () {
    $.getScript('https://cdn.vernacular.ai/vernacular.sdk.e750206d.js', function() {
      window.vernacular.api.init({ 
        accessToken: '511c8843-382f-4a5a-a476-ba0b70200817',
        themeColor: '#FF3E1B',
        hasChatBotButton: false,
        hasPushNotificationEnable: false,
        autoPopupEnable: 1,
        autoPopupTimeout: 5,
      });
    });
    
    // this will display the notification after 2sec
    animatePop();
  });
</script>
```

> Note: By setting hasChatBotButton and hasPushNotificationEnable to false, the default circular chat button and push notification will not be visible.

**3-** Use following method to open the chatbot (implementation will be same as the current deployed code).

```
window.vernacular.api.openChatBot()
```

**4-** We have implemented methods that will get trigger whenever state of bot will change means either from open to close or from close to open. These will be helpful to hide/show the custom chatbot button and notification `div`, use the following code snippet:

```
// use the given code snippet

<script type='text/javascript'>
  window.vernacular.api.onChatBotOpen = function() {
     changeVisibility('none')
  }
  
  window.vernacular.api.onChatBotClose = function() {
    // this will animate the notification div
    animatePop();
    
    changeVisibility('')
  }
  
  function changeVisibility (value) {
    const tooltip = document.querySelector('.vernacular-web-sdk-notification-tooltip')
    if (tooltip) {
      tooltip.style.display = value
    }

    const webChatElement = document.querySelector('.vernacular-web-sdk-chat-element')
    if (webChatElement) {
      webChatElement.style.display = value
    }
  }
</script>
```

Full Code:
=========

```
<script type='text/javascript'>
  $(document).ready(function () {
    $.getScript('https://cdn.vernacular.ai/vernacular.sdk.e750206d.js', function() {
      
      window.vernacular.api.init({ 
        accessToken: '511c8843-382f-4a5a-a476-ba0b70200817',
        themeColor: '#FF3E1B',
        hasChatBotButton: false,
        hasPushNotificationEnable: false,
        autoPopupEnable: 1,
        autoPopupTimeout: 5,
      });

      window.vernacular.api.onChatBotOpen = function() {
        changeVisibility('none');
      }
      
      window.vernacular.api.onChatBotClose = function() {
        // this will animate the notification div
        animatePop();
        
        changeVisibility('');
      }
    });
    
    // this will display the notification after 2sec
    animatePop();
  });


  document.querySelector('.chat').addEventListener('click', function () {
    window.vernacular.api.openChatBot();
  });
  document.querySelector('.mob-chat').addEventListener('click', function () {
    window.vernacular.api.openChatBot();
  });
  document.querySelector('.chat-with').addEventListener('click', function () {
    window.vernacular.api.openChatBot();
  });
  document.querySelector('.mobile-exide-chat').addEventListener('click', function () {
    window.vernacular.api.openChatBot();
  });


  function animatePop() {
    $(".exide-chat-bot_1").css({ bottom: '10vh', opacity: '0' });
    setTimeout(function (){
        $(".exide-chat-bot_1").css({bottom:'15.7vh',opacity:'1'});
    }, 2000);
  }
  
  function changeVisibility (value) {
    const tooltip = document.querySelector('.vernacular-web-sdk-notification-tooltip')
    if (tooltip) {
      tooltip.style.display = value;
    }

    const webChatElement = document.querySelector('.vernacular-web-sdk-chat-element')
    if (webChatElement) {
      webChatElement.style.display = value;
    }
  }

</script>
```

Kindly refer the Web SDK [doc](https://gist.github.com/MayankShukla5031/ea4a7278edecc0c84d49fdbce16b956c) for all other properties and methods.


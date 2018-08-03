Overview
========
Vernacular.ai Web SDK helps you provide a rich messaging experience to your website visitors. It allows you to select from multiple configuration options to rapidly prototype according to your user needs.

Web SDK comes with:
* Quick integration
* Voice-to-Text support for multiple Indian languages
* Mobile focused conversational design elements
* Optimised connection management for slow (2G friendly) internet
* Configurable Bot name, logo and theme as per the brand requirements
* More control over user engagement using in-conversation messages and contextual push-notifications

Setup
=====
Include the following snippet at the end of the <body> tag to setup the Bot with default configuration.

```JavaScript
<div class="vernacular-web-sdk"></div>
<script defer src="CDN_SDK_URL" onload="vernacularSDKInit()"></script>
<script defer type="text/javascript">
  function vernacularSDKInit() {
    window.vernacular.api.init({
      accessToken: BOT_ACCESS_TOKEN
    })
  }
</script>
```

It will load the script from the specified URL without blocking the HTML parsing in the DOM. This ensures that the script is executed only when parsing has finished.

An instance of Web SDK will be created using the configuration specified in the call to init method. The parameter accessToken is mandatory, its value BOT_ACCESS_TOKEN is used to identify the scope and authenticate the bot.

> Refer to the next section for all the configuration options.


Configuration
=============

Vernacular.ai Web SDK provides a seamless way of customizing the Bot properties so that you can serve a familiar experience to your visitors.

The configuration can be done by providing a JSON structure of key-value pairs as a parameter to the init method.

## Methods
> All the methods will be accessible by `window.vernacular.api` object.

### isChatBotOpen
This method will return a `boolean` value (true/false), the current status of the chatbot.

### openChatBot
This a way to open the chatbot programatically means any time you can call the method to open the chatbot. Nothing will happen if chatbot will be already in open state.

### closeChatBot
This method will be helpful to close the chatbot on any specific event.

### onChatBotOpen
This will be a place where you can perform additional task/operation whenever chatbot will open.

Snippet:

```
window.vernacular.api.onChatBotOpen = function() {
  console.log('We are here to answer all your queries, please ask :)')
}
```

### onChatBotClose
A method that will get called whenever chatbot will be closed.

Snippet:

```
window.vernacular.api.onChatBotClose = function() {
  console.log('chat bot has been closed.')
}
```

### init
This method creates an instance of the SDK and renders the widget in the given page, it accepts a JSON object with key-value pairs to configure the workflow.

## Properties
> Properties not specified in the configuration will use their default values.

### accessToken
###### required
Unique `string` (UUID-v4) used to authentication and identify the scope of the Bot.

### themeColor
###### default: "#787eff"
A `string` value representing the Hex color-code aligning with the website theme.

Snippet:

```JavaScript
window.vernacular.api.init({
  accessToken: BOT_ACCESS_TOKEN,
  ...
  themeColor: "#787eff",
  ...
})
```

### botName
###### default: "Chat Support"
A `string` value to change the Bot name (in header and push-notification). It has a maximum length limit of 18 characters.

### botImage
URL field that can be used to change the default bot image, It expect a complete image url.

### headerColor
###### default: "#5a5766"
A `string` value representing the Hex color-code, to customize the chatbot header color.

### fontColor
###### default: "#ffffff"
A `string` value to customize the font color of the "user messages" according to the theme.

List of possible values:
* `"#ffffff"` - suitable for dark theme colors.
* `"#5a5766"` - suitable for light theme colors.

### hasChatBotButton
###### default: true
A `boolean` value to control the visibility of chatbot circular button. This will be helpful to use a custom button or any other ui element instead of the default one.

### autoPopupEnable
###### default: 0
An `integer` value to specify whether Bot will open automatically after certain interval (`autoPopupTime`) or not.

List of possible values:
* `0` - disable for all
* `1` - enable auto pop-up only for website size screens (not for mobile devices)
* `2` - enable auto pop-up for all screen sizes

### autoPopupTimeout
###### default: 15
An `integer` value (in seconds) to specify the interval after which bot will automatically open.

### nextPopupTimeout
###### default: 12
An `integer` field (in hours), using this field we can control the repetition of auto pop-up. Auto pop-up will be disabled for that period of time.

### enableInChatNotification
###### default: false
A boolean value We have a feature of showing notification in the chat itself such as asking user to enter/ask the query if he is inactive for certain period.

### inChatNotificationTime
###### default: 30
An `integer` field (in seconds) to specify the interval after which in chat notification will appear.

### hasPushNotificationEnable
###### default: true
A boolean field to control the push notifications, Push notification displays the help text (default messages), but we can customize the text using `pushNotificationText` property.

### pushNotificatiomTimeout
###### default: 10
An `integer` value (in seconds) to specify the interval after which push notification will be displayed.

### pushNotificationDuration
###### default: 5
An `integer` value (in seconds) to specify the time for which push notification will be shown, it will disappear after that period.

### nextPushNotificationTimeout
###### default: 12
An `integer` field (in hours), using this field we can control the repetition of push notification. Push notification will be disabled for that period of time.

### pushNotificationText
###### default: 

```JavaScript
{
  "en": "Hey there! You can chat with me for any assistance, would be happy to help!",
  "hi": "नमस्ते! किसी भी प्रकार की सहायता के लिए आप मुझसे यहाँ चैट कर सकते हैं !",
  "eh": "Namaste! Aap apna koi bhi sawal yaha chat par mujhse puch sakte hain!"
}
```
  
An `object` field to customize the push notification text, you need to specify the message for the language you want to customize (it will be merged with default messages for other languages). English text will be displayed by default.

### inChatNotificationMessages
###### default: 

```JavaScript
{
  "en": "Hey there! You can chat with me for any assistance, would be happy to help!",
  "hi": "नमस्ते! किसी भी प्रकार की सहायता के लिए आप मुझसे यहाँ चैट कर सकते हैं !",
  "eh": "Namaste! Aap apna koi bhi sawal yaha chat par mujhse puch sakte hain!"
}
```
  
An `object` field to customize the in chat notification text, specify the language code and its message (it will be merged with default messages for other languages, means mention the code for which you want to customize). English text will be displayed by default.

Language code:

```JavaScript
Hindi    - "hi"
English  - "en"
Hinglish - "eh"
```

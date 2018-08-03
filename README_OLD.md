# web-sdk
Web SDK for chatbots built on vernacular.ai's platform

### Vernacular.ai Web SDK Integration

#### Stylesheet

Include the following code snippet at the end of the `<head>` tag.

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.2.2/semantic.min.css"></link>
```

#### JavaScript

---

Include the following code snippet at the end of the `<body>` tag.

```html
<div class="vernacular-web-sdk"></div>
<script type="text/javascript" src="CDN_SDK_URL"></script>
<script type="text/javascript">
window.vernacular.renderChat({
  'accessToken': 'BOT_ACCESS_TOKEN',
  'themeColor': 'THEME_COLOR',
  'popupTimeout': 'POPUP_TIMEOUT',
  'pushMessageTimeout': 'PUSH_MESSAGE_TIMEOUT'
});
</script>
```

#### Parameters

##### CDN\_SDK\_URL
Versioned URL for the Web SDK, served from Vernacular.ai Content Delivery Network.

##### BOT\_ACCESS\_TOKEN
Custom access token used for authentication and defining the scope.

##### THEME\_COLOR
The color code (in hex, such as #FF3E1B) suitable for the website.

##### POPUP\_TIMEOUT

The delay (in milliseconds) before the initial auto pop-up.

> Disabled for mobile devices

```html
<!--For a 5 second delay between the loading and the popup-->
...
'popupTimeout': '5000',
...
```

##### PUSH\_MESSAGE\_TIMEOUT
The inactivity period (in milliseconds) after which an in-conversation push message will be delivered to the user's conversation.

> There will be only one in-conversation push message per tab

```html
<!--To send the message to a user who was inactive for 10 seconds after the last interaction-->
...
'pushMessageTimeout': '10000',
...
```

# Use the following JavaScript in Storyline
## Download the JavaScript files in this repository to place in your published folder. You will need to edit the LRS details in the xapi.js file.

```
// Script that appends scripts to body of Storyline file

var appendBody = '<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script><script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/3.1.9-1/crypto-js.min.js"></script><script type="text/javascript" src="xapiwrapper.min.js"></script><script src="xapi.js"></script>';

// Append the header with the code contained in the variable

$('body').append(appendBody);


// Statement function without results field

sendStatement('http://adlnet.gov/expapi/verbs/experienced','experienced','http://example.com/activity-id','main page','in accordion example');
```

# Page views in Rise - Use the following JavaScript in the published Rise index.html file
## Download the JavaScript files in this repository to place in your published folder at the end before the closing body tag. You will need to edit the LRS details in the xapi.js file.


```
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script><script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/3.1.9-1/crypto-js.min.js"></script><script type="text/javascript" src="xapiwrapper.min.js"></script><script src="xapi.js"></script>

<script>

function pageAccessed() {
  setTimeout(function() {
    var page = window.location.href;
      if (document.URL.indexOf("PUT YOUR PAGE URL HERE") === 0) {

        sendStatement('http://adlnet.gov/expapi/verbs/experienced','experienced',page,'Some page','in Rise Course');
      }
    }, 1000);
  }

window.addEventListener('load', pageAccessed, false);
window.addEventListener('hashchange', pageAccessed, false);

</script>
```
# Rise with page views and clicks - Use the following JavaScript in the published Rise index.html file
## Download the JavaScript files in this repository to place in your published folder at the end before the closing body tag. You will need to edit the LRS details in the xapi.js file.

```
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/3.1.9-1/crypto-js.min.js"></script>
    <script type="text/javascript" src="xapiwrapper.min.js"></script>
    <script src="xapi.js"></script>

<script>

function pageAccessed() {
  setTimeout(function() {
    var page = window.location.href;

    if (document.URL.indexOf("PUT YOUR PAGE URL HERE") === 0) {

      sendStatement('http://adlnet.gov/expapi/verbs/experienced','experienced',page,'Gauging your wellness','in Rise Course');
    }
    if (document.URL.indexOf("PUT YOUR PAGE URL HERE") === 0) {

      sendStatement('http://adlnet.gov/expapi/verbs/experienced','experienced',page,'Stretching for success','in Rise Course');
    }
    if (document.URL.indexOf("PUT YOUR PAGE URL HERE") === 0) {

      sendStatement('http://adlnet.gov/expapi/verbs/experienced','experienced',page,'Stress','in Rise Course');
       clickHandler('.blocks-tabs__header-item', page, 'tab');  // Tracking click on tabbed components
       clickHandler('.blocks-accordion__item', page, 'accordion');  // Tracking click on accordion components
    }
  }, 1000);
}

function clickHandler(itemClassName, page, pageName) {
  var $items = $(itemClassName);
  $items.each(function(i) {
    var num = i + 1;
    $(this).attr('data-name', pageName + '-' + num);
    $(this).on('click', function() {
      var dataAttr = $(this).attr('data-name');
      sendStatement('http://adlnet.gov/expapi/verbs/experienced', 'experienced', page + '?' + dataAttr, dataAttr, 'in Rise Course');
    });
  });
}

window.addEventListener('load', pageAccessed, false);
window.addEventListener('hashchange', pageAccessed, false);

</script>
```

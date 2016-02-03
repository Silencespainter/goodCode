#Vanilla Javascript
## Functions
  ~~~
  nameOfFunction();
  ~~~

### Types
  ~~~
  Functions of JS: alert();
  Functions of Customize: iLikeThisFunction();
  ~~~


## Variables
  ~~~
  1. myVar
  2. _myVar
  3. $myVar
  ~~~


# Vanilla Javascript vs jQuery
## DOM Selectors

### ID
  ~~~
  // JS => All
  getElementById('nameOfID');

  // JQUERY
  $('#nameOfID');
  ~~~

### Class
  ~~~
  // JS => +IE9
  document.getElementsByClassName('nameClass');

  // JQUERY
  $('.nameClass');
  ~~~

### Tagname
  ~~~
  // JS => +IE6
  document.getElementsByTagName('h1');

  // JQUERY
  $('h1');
  ~~~

### Others
  ~~~
  // JS => +IE8
  document.querySelector('.nameClass');
  ~~~


## DOM Manipulation
### Adding content
  ~~~
  // JS => ALL
  document.getElementById("container").innerHTML += "<p>more content</p>";

  // JQUERY
  $('#container').append("<p>more content</p>");
  ~~~

###  Remove element from the DOM
  ~~~
  // JS => ALL
  var c = document.getElementById("container");
  c.parentNode.removeChild(c);

  // JQUERY
  $("#container").remove();
  ~~~


# Good practices with jQuery

## Naming jQuery object starting with $
  ~~~
  // NOT
  var form = $('#contactForm');
 
  // YES
  var $form = $('#contactForm');
  ~~~
## Using $this
  ~~~
  // NOT
  $('li').each(function() {
  	$(this).on('click', function() {
      	$(this).addClass('active');
  	});
  });

  // YES
  $('li').each(function() {
   	var $this = $(this);
   	$this.on('click', function() {
        	$this.addClass('active');
   	});
  });
  ~~~

## Caching jQuery objects

  ~~~
  // NOT
  $('.menu li').each(function() { ... });
  $('.menu li').each(function() { ... });

  // YES
  var $items = $('.menu li');
  $items.each(function() { ... });

  // REUSE IT
  $items.each(function() { ... });
  ~~~

## Chaining method
  ~~~
  // NOT
  var $a = $('#about');
  $a.hide();
  $a.addClass();
  $a.fadeIn();
  $a.hide();

  // YES
  $('#about').hide().addClass().fadeIn().hide();

  // BETTER
  $('#about')
  	.hide()
  	.addClass()
  	.fadeIn()
  	.hide();

  ~~~
## Creating new element
  ~~~
  // NOT
  var $hidden = $('<input class="form-control" type="hidden" name="foo" value="bar" />').appendTo('#form');

  // YES
  var $hidden = $('<input/>')
              	.addClass('form-control')
              	.attr('type', 'hidden')
              	.attr('name', 'foo')
              	.val('bar')
              	.appendTo('#form');
   ~~~
   
## Optimizing selectors

### Using ID selector
  ~~~
  // NOT
  $('#wrapper #inner');
  $('div#inner');
  $('.wrapper #inner');

  // YES
  $('#inner');
  ~~~

### Using ID-based selector
  ~~~
  // NOT
  $('#container .row');

  // FASTER
  $('#container').find('.row');
  ~~~

### Avoid implied universal selectors
  ~~~
  // NOT
  $('.category :radio');

  // YES
  $('.category input:radio');
  ~~~

### Using filtering methods instead of pseudo selectors
  ~~~
  // NOT
  $('.item:first')

  // YES
  $('.item').eq(0)
  ~~~

### Using custom namespace for events
  ~~~
  // NOT
  $('#saveButton').on('click.bv', function() {
  	...
  });

  // YES
  // Later, it's possible to unbind the event handler
  $('#saveButton').off('click.bv');
  ~~~

### Don't put all parameters in Ajax URL
  ~~~
  // NOT
  $.ajax({
  	url: '/remote/url?param1=value1&amp;param2=value2...'
  }});

  // YES
  $.ajax({
  	url: '/remote/url',
  	data: {
      	param1: 'value1',
      	param2: 'value2'
      	...
  	}
  })
  ~~~

### Use string concatenation or array.join() over .append()
  ~~~
  // NOT
  var $myList = $("#list");
  for(var i = 0; i < 10000; i++){
  	$myList.append("<li>"+i+"</li>");
  }
  // FASTER
  var superArray = [];
  for(var i = 0; i < 10000; i++){
  	superArray[i] = "<li>"+i+"</li>";
  }
  $myList.html(superArray.join(''));
  ~~~

### Document ready event handler should not be an anonymous function
  ~~~
  // NOT // You can never reuse or write a test for this function.
  $(function(){ ... });

  // YES
  $(initPage); // or $(document).ready(initPage);
  function initPage(){
  	// Page load event where you can initialize values and call other initializers.
  }
  ~~~

### Sample Ajax Template
  ~~~
  var jqxhr = $.ajax({
  	url: url,
  	type: "GET", // default is GET but you can use other verbs based on your needs.
  	cache: true, // default is true, but false for dataType 'script' and 'jsonp', so set it on need basis.
  	data: {}, // add your request parameters in the data object.
  	dataType: "json", // specify the dataType for future reference
  	jsonp: "callback", // only specify this to match the name of callback parameter your API is expecting for JSONP requests.
  	statusCode: { // if you want to handle specific error codes, use the status code mapping settings.
      	404: handler404,
      	500: handler500
  	}
  });
  jqxhr.done(successHandler);
  jqxhr.fail(failureHandler);
  ~~~

### Use Object literals for parameters
  ~~~
  // NOT // 3 calls to attr()
  $myLink.attr("href", "#").attr("title", "my link").attr("rel", "external");

  // BETTER // only 1 call to attr()
  $myLink.attr({
  	href: "#",
  	title: "my link",
  	rel: "external"
  });
  ~~~

### Others
  ~~~
  // OK
   $("document").ready(function() {
  	// The DOM is ready!
  	// The rest of the code goes here
	});
    
  // BETTER
  $(function() {
  	// The DOM is ready!
  	// The rest of the code goes here
	});
  ~~~

### Save loop's length
  ~~~
  var myLength = myArray.length;

  for (var i = 0; i < myLength; i++) {
  	// do stuff
  }
  ~~~

### Add content in loop
  ~~~
  // NOT
  $.each(myArray, function(i, item) {
 	var newListItem = '<li>' + item + '</li>';
 	$('#ballers').append(newListItem);
  });

  // BETTER
  var frag = document.createDocumentFragment();
  $.each(myArray, function(i, item) {
  	var newListItem = '<li>' + item + '</li>';
  	frag.appendChild(newListItem);
  });
  $('#ballers')[0].appendChild(frag);

  // COOL
  var myHtml = '';
  $.each(myArray, function(i, item) {
  	myHtml += '<li>' + item + '</li>';
  });
  $('#ballers').html(myHtml);
  ~~~

### Don't repeat yourselft
  ~~~
  // NOT
  if ($eventfade.data('currently') != 'showing') {
  	$eventfade.stop();
  }
  if ($eventhover.data('currently') != 'showing') {
  	$eventhover.stop();
  }
  if ($spans.data('currently') != 'showing') {
  	$spans.stop();
  }

  // YES
  var $elems = [$eventfade, $eventhover, $spans];
  $.each($elems, function(i,elem) {
  	if (elem.data('currently') != 'showing') {
      	elem.stop();
  	}
  });
  ~~~

### Beware Anonymous Functions
  ~~~
  // NOT
  $( document ).ready(function() {
  	$( "#magic" ).click(function( event ) {
      	$( "#yayeffects" ).slideUp(function() {
          	// ...
      	});
  	});
  	$( "#happiness" ).load( url + " #unicorns", function() {
      	// ...
  	});
  });

  // BETTER
  var PI = {
  	onReady: function() {
      	$( "#magic" ).click( PI.candyMtn );
      	$( "#happiness" ).load( PI.url + " #unicorns", PI.unicornCb );
  	},
  	candyMtn: function( event ) {
      	$( "#yayeffects" ).slideUp( PI.slideCb );
  	},
  	slideCb: function() { ... },
  	unicornCb: function() { ... }
  };
  $( document ).ready( PI.onReady );
  ~~~


---
*Reference*

    1. <http://www.sitepoint.com/jquery-vs-raw-javascript-1-dom-forms/>
    2. <http://formvalidation.io/news/best-jquery-practices/>
    3. <http://lab.abhinayrathore.com/jquery-standards/>



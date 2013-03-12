---
layout: post
title: My Journery So Far Making The Personality Profile Quiz
---

{{ page.title }}
================

A few months ago, my friends &amp; I get together and started an IT project that sought to replace papers with everything digital (online). A demo of my part is available [here](http://jhkueh.github.com/demo-formUI-esc/index.html). Since it was a church's project, we all volunteered our time and meet at Joseph's, the project manager, place about once every fortnight to get some serious work done. The project will be running on a LAMP stack. As most of us (6) didn’t know PHP, to accelerate the development, we had Joppy (a PHP web developer) in our group to teach and lead us.

### Why is this IT project necessary?  ###

Previously, participants of a particular leadership training course in our organisation have to fill in several paper forms (at least 5) at the end. The end result would be an analysis of your personality, gifts and talents. These forms were manually processed by the training coordinator alone. Often tedious and repetitive, these tasks are very much suited for a computer. It would not be much problem to handle 5 participants’ submission. However, the current solution would not scale very well to handle 30+ participants, needless to say, 100+ participants (the anticipated participants).

### Thus was born the IT ministry ###

Joseph was the guy who gathered us together and instilled the vision to us. We all agreed to volunteer our talents and to serve. As for me, in addition to that, I see it as a great opportunity to get my foot in the door in web development. 

As for our team structure, we had a small team (7 developers) and each of us works in pairs with each pair having a person at least having been exposed to PHP and web development. I was fortunate enough to pair up with Tim. Besides Joppy, he is the only other web developer in our team, with a year’s experience working as a .Net developer. On the other hand, I had completed Udacity’s [Web Development](https://www.udacity.com/course/cs253) course which was taught by Steff Huffman (co-founder of [reddit](http://reddit.com). From there, I had written a blog and wiki application from the ground-up with Python. So, I thought that it should be easy to learn PHP and complete our task with Tim around. Boy, was I wrong. 

### It took longer than expected (underestimated), but I learn a lot ###

Each pair of us picked a module to work on (from the backend to the frontend). Tim picked the most complex module (personality profile quiz) which has been a good learning experience. The form had 20+ questions and each question has 2 columns (_Most_ &amp; _Least_) of 4 rows answers to choose from. So a user has to select an answer from the _Most_ &amp; _Least_ columns each and answers from the same rows cannot be selected twice. Here's the origianl form:

![original form](http://dl.dropbox.com/u/72768665/github/2013.03.12/original_form.png "original form")

At first, I wondered if I should make a sprite of the symbols to render the answers, just like how *Twitter Bootstrap* uses *Icon glyphs*. Then, Tim pointed out that having the symbols would influence users to fill the form with bias, which makes sense. So, they got replaced with radio buttons instead.

![radio buttons](http://dl.dropbox.com/u/72768665/github/2013.03.12/radio_buttons.png "radio buttons")

Next, how do we make sure that users only select an answer from the same row? And not this:

![radio buttons error](http://dl.dropbox.com/u/72768665/github/2013.03.12/radio_buttons_err.png "radio buttons error")

Tim assured me that it can be done with jQuery. Sure, why not? I  was using Bootstrap for this module and Bootstrap uses jQuery for some of its components to work. However, I didn’t know jQuery at all, although I know a little bit of JavaScript (since it’s similar to C &amp; C++).

Part of our discussion also centred on the UI/UX of the web form. Initially, I thought of disabling the radio button of the other column in the same row when a radio button is selected. But, Tim pointed out that it would be better to have the _latest selected_ radio button selected instead. So, for example, if the radio button (row 1, column 1) is selected and then the other radio button is selected in the next column (row 1, column 2), the former radio button (row 1, column 1) will be unselected first and then the later button selected (row 1, column 2) [demo below]. Which to me, is a very valid point. Make it less action to get things done, easier for the user. Just like Amazon’s 1-click.

So in my spare time, I google around and found this stack*overflow* [answer](http://stackoverflow.com/a/12526143) which is similar to what I’m trying to do. After modifying and debugging the code (which took a whole evening), I got it to work:

![demo](http://dl.dropbox.com/u/72768665/github/2013.03.12/animate_radio.gif "demo")

Here’s the JS source code:

```javascript
    $("td#tdR").click(function () {
  		var grID = $(this).find('input:radio').attr('id');
		  var grName = $(this).find('input:radio').attr('name');
		  var teGrp = grName;
		  if (grName.indexOf('M') == -1) { // don't have 'M' in grName
  			teGrp = grName.replace('L', 'M');
		  } else {
  			teGrp = grName.replace('M', 'L');
		  }
		  var getAttr = $(':radio[name='+teGrp+'][id='+grID+']').is(':checked');
		  if (getAttr != true) {
  			$(':radio[name='+grName+'][id='+grID+']').prop('checked', true);
		  } else {
  			$(':radio[name='+teGrp+'][id='+grID+']').prop('checked', false);			
			$(':radio[name='+grName+'][id='+grID+']').prop('checked', true);
		  }
    });
```

And here’s the optimised code (after I read about efficient css selector from [csswizardry](http://csswizardry.com/)):

```javascript
	$("td#tdR").click(function () {
		var curTD = $(this);
		var curRD = curTD.find('input[type=radio]');
		var grID = curRD.attr('id');
		var grName = curRD.attr('name');
		var teGrp = grName;
		if (grName.indexOf('M') == -1) { // don't have 'M' in grName
			teGrp = grName.replace('L', 'M');
		} else {
			teGrp = grName.replace('M', 'L');
		}
		var othRD = curTD.parent().find('input[type=radio][name='+teGrp+'][id='+grID+']');
		var getAttr = othRD.is(':checked');
		if (getAttr) {
			othRD.prop('checked', false);
		}
		curRD.prop('checked', true);
	});
```

Well, that's the progress so far. I'd recently added an alert message with instructions on how to fill the form (need to ask Tim's opinion on this). I also plan to improve the UI of the tabs in the [form](http://jhkueh.github.com/demo-formUI-esc/index.html). Apart from that, I still need to write the result page of the form. It will have line charts powered by D3.js. That's the idea at the moment. Things might changed. Afterall, I still got plenty to learn about making a great web app. If it wasn't for Tim, the [demo](http://jhkueh.github.com/demo-formUI-esc/index.html) that you see now will be pretty much like the ones in the original paper form.

--
<p class="meta">12 March 2013</p>

Download Link: https://assignmentchef.com/product/solved-sdev-lab-9-web-services
<br>


 <main class="container" role="main"></main>



<span class="kksr-muted">Rate this product</span>

<p class="lead">In this lab, we will use a REST API to create webpage to display today’s weather. You will edit the template (below) which includes all of the files necessary to work with REST. To receive credit for this lab, you MUST complete steps 1 and 3 in recitation and get marked off by your TA. You must upload “lab_9_link.txt” to Canvas by the deadline.

<p class="h5"><a href="./Web_Services_Starter_Files.zip">Download </a>the template and make sure you extract the files before using them.

<b><u>NOTE:</u></b> This lab is due next week, right before recitation.

<table class="table">

 <tbody>

  <tr>

   <th class="h5">Est. Time &#x23f1;</th>

  </tr>

  <tr>

   <td class="h5"><span id="eta">0</span> minutes</td>

  </tr>

 </tbody>

</table>

<p class="alignleft h5">Lab Overview

<button class="btn btn-primary btn-sm alignbtn" type="button">Mark Complete</button> <button class="btn btn-primary btn-sm alignbtn" type="button" data-toggle="collapse" data-target="#multiCollapseExample1" aria-expanded="false" aria-controls="multiCollapseExample1">Expand</button>

For today’s lab, you will be completing the starter weather.html web page so that it can access the DarkSky API and display today’s weather and the 6 day future forecast. All of the necessary html code has been provided for you. All you have to do is complete the javascript at the bottom of weather.html. You can see an example of a completed weather.html web page below.



<hr>

<img decoding="async" alt="An Example of a completed Weather Page" data-src="img/weather_webpage.png" class="img-fluid lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" class="img-fluid" src="img/weather_webpage.png" alt="An Example of a completed Weather Page">

 </noscript>

<p class="alignleft h5">1. Set up A DarkSky Account

In order to access DarkSky’s weather inforamtion, you’ll need to create a free account. Note, the free account only allows you to make 1,000 API calls per day. This is more than enough for today’s lab, but be aware if you decide to work with DarkSky or other API’s on your group project, these API’s will have similiar restrictions. If your code makes a lot of automated API requests (say in a for/while loop), you may quickly run out of API requests while testing your app!



<dl>

 <dt>

  1. Register at <a href="https://darksky.net/dev" target="_blank" rel="noopener">DarkSky.net</a>

 </dt>

 <dd></dd>

</dl>

<dl>

 <dt>

  2. Login and Find Your API Access Key

 </dt>

 <dd></dd>

</dl>

<img decoding="async" alt="The registration page for DarkSky" data-src="img/register.png" class="img-fluid lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

<noscript>

 <img decoding="async" class="img-fluid" src="img/register.png" alt="The registration page for DarkSky">

</noscript>

Head over to the <a href="https://darksky.net/dev/register" target="_blank" rel="noopener">registration page</a> and enter in your email &amp; password information to register for a new account.

<img decoding="async" alt="The registration page for DarkSky" data-src="img/account_page.png" class="img-fluid lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

<noscript>

 <img decoding="async" class="img-fluid" src="img/account_page.png" alt="The registration page for DarkSky">

</noscript>

After you login you’ll find your API access key (Please note the one in the image is invalid/old. Don’t use it! It won’t work!). Make sure to either keep this tab open or save your “Sample API Call” URL. We’ll be using it later on in our weather.html’s javascript code.

<p class="alignleft h5">2. Make API Requests

<p class="alignright h5">

In this section, we’ll cover how your javascript code will make a request to the DarkSky API

<hr>

<dl>

 <dt>

  1. Make a DarkSky API Request with Ajax and Jquery

 </dt>

 <dd>

  <pre class="row"><code class="language-js">$(document).ready(function() {	var url =''; //Place your DarkSky API Call Here	$.ajax({url:url, dataType:"jsonp"}).then(function(data) {	})})</code></pre>

  <dl class="row">

   <dt class="col-sm-2">

    var url = ”

   </dt>

   <dd class="col-sm-10">

    Inside of the single quotes ”, you’ll need to add the API URL you saved from DarkSky. This is listed in the “Sample API Call” as https://api.darksky.net/forecast/[key]/[latitude],[longitude]

   </dd>

   <dt class="col-sm-2">

    $.ajax({…

   </dt>

   <dd class="col-sm-10">

    To access DarkSky’s data, we’ll use ajax to make a call to our url for json information. The key part here is that our call will return a json object called data. The data object will include the current weather and future weather information listed by the hour or day. Checkout a sample response <a href="https://darksky.net/dev/docs#forecast-request">here</a>

   </dd>

  </dl>

 </dd>

 <dt>

  2. Display Your Weather Data

 </dt>

 <dd>

  <pre class="row"><code class="language-js">$(document).ready(function() {	var url =''; //Place your DarkSky API Call Here	$.ajax({url:url, dataType:"jsonp"}).then(function(data) {		console.log(data);//Review all of the data returned		console.log("Current Temp: " + data.currently.apparentTemperature);//View Today's Temp		console.log("Tomorrow's High: " + data.daily.data[1].apparentTemperatureHigh);//View Tomorrow's High	})})</code></pre>

  <dl class="row">

   <dt class="col-sm-4">

    console.log(data);

   </dt>

   <dd class="col-sm-8">

    To review all of the data provided by DarkSky, we’ll print it out to the console. Open your Web Browser and you can see all of the fields loaded into our JSON data. The main fields we will be concerned with our are currently (the curren weather) and daily (an 8 day forecast of weather information).

   </dd>

   <dt class="col-sm-4">

    data.currently.apparentTemperature

   </dt>

   <dd class="col-sm-8">

    To access the current weather information, we’ll need to use the following format: data.currently.FIELD_NAME. In this example, we are retrieving the current temperature.

   </dd>

   <dt class="col-sm-4">

    data.daily.data[1].apparentTemperatureHigh

   </dt>

   <dd class="col-sm-8">

    To access the future weather information we’ll need to access the daily field’s data array. The data array contains 8 days of information (starting with today’s information). In the example, we are grabbing the estimated high temperature for tomorrow which means we’ll need to use index [1] (index 0 is the current day’s information).

   </dd>

   <dt class="col-sm-4">

    Complete List of Data Point Fields

   </dt>

   <dd class="col-sm-8">

    DarkSky provides far more information than what we’ll need for today’s lab. To see all of the types of information you can retrieve, checkout the documentation’s complete list of data point fields <a href="https://darksky.net/dev/docs#data-point-object">here</a>

   </dd>

  </dl>

 </dd>

 <dt>

  3. Working with Unix Timestamps

 </dt>

 <dd>

  <pre class="row"><code class="language-js">$(document).ready(function() {	var url =''; //Place your DarkSky API Call Here	$.ajax({url:url, dataType:"jsonp"}).then(function(data) {		console.log(data);//Review all of the data returned		console.log("Current Temp: " + data.currently.apparentTemperature);//View Today's Temp		console.log("Tomorrow's High: " + data.daily.data[1].apparentTemperatureHigh);//View Tomorrow's High		var unix_time = data.currently.time;//Retrieve the current timestamp		var javascript_time = new Date(unix_time * 1000);//Convert the unix time stamp to javascript		console.log(javascript_time);		console.log(javascript_time.getDay());	})})</code></pre>

  <dl class="row">

   <dt class="col-sm-4">

    unix_time * 1000

   </dt>

   <dd class="col-sm-8">

    DarkSky provides the timestamps for each weather forecast datapoint, but we can’t use this information as-is. This is because DarkSky returns a Unix timestamp (in seconds) but in javascript our Date class works in milliseconds! So to convert the Unix timestamp, we need to multiply it by 1,000.

   </dd>

   <dt class="col-sm-4">

    console.log(javascript_time);

   </dt>

   <dd class="col-sm-8">

    The complete timestamp will list the provided date and time.

   </dd>

   <dt class="col-sm-4">

    javascript_time.getDay()

   </dt>

   <dd class="col-sm-8">

    If we want to pull out individual parts of our timestamp, we’ll need to use the various get() methods provided by the Date Class. In this example we are using the .getDay() method which returns the day of the week. As you can see, the value returned is a number between 0 &amp; 6, where 0 represents Sunday and 6 represents Saturday.

   </dd>

   <dt class="col-sm-4">

    Complete List of Date Methods

   </dt>

   <dd class="col-sm-8">

    If you want to learn more about working with Javascript Dates, check out W3Schools tutorial <a href="https://www.w3schools.com/jsref/jsref_obj_date.asp">here</a>

   </dd>

  </dl>

 </dd>

</dl>

<p class="alignleft h5">3. Updating the weather.html

<button class="btn btn-primary btn-sm alignbtn" type="button">Mark Complete</button> <button class="btn btn-primary btn-sm alignbtn" type="button" data-toggle="collapse" data-target="#multiCollapseExample4" aria-expanded="false" aria-controls="multiCollapseExample4">Expand</button>

<p class="alignright h5">(<span id="time4" class="time">40</span> Minutes)

In order to display the information from the DarkSky API call in weather.html, you will have to write some javascript to dynamically fill in the weather values (e.g., Precipitation, Humidity, etc.)



<dl>

 <dt>

  1. Make an DarkSky API request to retreive the weather information

 </dt>

 <dd>

  <pre>Retrieve the following information from the <b>DarkSky API</b>:1. image_today : This should display an image for today's weather.      You will have to match the data.currently.icon to an image in the /img directory2. icon_today : This should display the value of data.currently.icon3. temp_today : This should display the current temperature (i.e., data.currently.temperature).4. thermometer_inner : Modify the height of the thermometer to match the current temperature.      You will have to modify the CSS in the &lt;style&gt; tags at the top of the weather.html file.      (i.e., #thermometer_inner { width: 95%; height: 20%; margin:2.5%; background: red; position:absolute; bottom:0;})      If the temperature is 32 F, then the thermometer will have a height of 32%.  Please note,      this thermometer has a lower boundary of 0 and upper boundary of 100.5. precip_today : This should display the current probability for precipitation and should be      listed as a % (i.e., data.currently.precipProbability).6. humidity_today : This should display the current humidity as a %.7. wind_today : This will display the current wind speed.8. summary_today: This will display the current summary for the day's weather.</pre>

 </dd>

 <dt>

  2. Process the daily forecast for the next 6 days

 </dt>

</dl>

<pre>    For the next 6 days you will need to add a new card listing:    1. The image icon for the day's weather    2. The temperature high    3. The temperature low</pre>

<dl>

 Each card should use the following format:




 <dd>

  <pre><code class="language-html">&lt;div class="col-2"&gt;  &lt;div class="card"&gt;    &lt;img class="card-img-top" src="Change to include the path of the image based on API data" alt="Card image caption"&gt;      &lt;div class="card-body"&gt;       &lt;h5 class="card-title"&gt;&lt;!-- List Day of the Week Here --&gt;        &lt;p class="card-text"&gt;High:&lt;!--List Temperature High --&gt;          Low: &lt;!-- List Temperature Low --&gt;</code></pre>




  <pre><code class="language-html">      &lt;/div&gt;   &lt;/div&gt;&lt;/div&gt;</code></pre>

 </dd>

</dl>

<dl>

 <dd></dd>

</dl>

<b><u>HINT:</u></b> – Make sure to use string concatenation to add the html code for the daily weather cards. This should be set to the innerHTML for the 6_day_forecast div.

<p class="alignleft h5">4. Submission Guidelines

<button class="btn btn-primary btn-sm alignbtn" type="button" data-toggle="collapse" data-target="#multiCollapseExample5" aria-expanded="false" aria-controls="multiCollapseExample5">Expand</button>

<dl>

 <dt>

  <ul>

   <li>Create a new github repo and upload Web_Services</li>

  </ul>

 </dt>

 <dd>

  <ol>

   <li style="list-style-type: none;">

    <ol>

     <li>On GitHub, create a new repository called Web_Services. Make sure you don’t overwrite any of the previous repos.</li>

     <li>Upload your Web_Services folder containing the entire directory structure for your website to GitHub.</li>

    </ol></li>

  </ol>

  <pre class="command-line" data-prompt="$"><code class="language-bash">git init #MAKE SURE YOU ARE IN THE FOLDER Web_Services AND NOT IN ANY OTHER FOLDER BEFORE YOU RUN git initgit add .git commit -m "Adding all of the files for lab 9"git push</code></pre>

 </dd>

 <dt>

  <ul>

   <li>Create a link to your GitHub repo</li>

  </ul>

 </dt>

 <dd>

  In a text file (lab_9_link.txt), write down the following:




  <ol>

   <li>Your name</li>

   <li>You partner’s name (if you have one)</li>

   <li>The link to your Web_Services Github Repo. (Make sure the repo is public!!!)</li>

  </ol>

 </dd>

 <dt>

  <ul>

   <li>Submit to Canvas</li>

  </ul>

 </dt>

 <dd>

  Submit your text file to Canvas. Make sure all submissions have been uploaded by the Deadline.

 </dd>

</dl>

<p class="alignleft h5">5. Bonus credits (15 points)

<button class="btn btn-primary btn-sm alignbtn" type="button">Mark Complete</button> <button class="btn btn-primary btn-sm alignbtn" type="button" data-toggle="collapse" data-target="#multiCollapseExample6" aria-expanded="false" aria-controls="multiCollapseExample6">Expand</button>

<dl>

 <dt>

  <ul>

   <li>Dynamically input the latitude and longitude based on user input (10 points)</li>

  </ul>

 </dt>

 <dd>

  <ol>

   <li>Create two text boxes and label them as Latitude and Longitude. This should allow the user to input the latitude and longitude of a city.</li>

   <li>On clicking the button ‘Check Weather’ the page should show the weather for the specified latitude and longitude.</li>

  </ol>

 </dd>

 <dt>

  <ul>

   <li>Change color of the thermometer based on the temperature (5 points).</li>

  </ul>

 </dt>

 <dd>

  <ol>

   <li>If temperature is normal the color of thermometer should be <span style="color: grey;">grey</span>.</li>

   <li>If temperature is above normal (greater than 85F) the color of thermometer should be <span style="color: red;">red</span>.</li>

   <li>If temperature is below normal (less than 65F) the color of thermometer should be <span style="color: blue;">blue</span>.</li>

  </ol>

 </dd>

</dl>

<p class="h4 text-center">Helper Icons
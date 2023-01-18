## 404 Status Code

<p class="p__1qg33Igem5pAgn4kPMirjw">
Let’s take a deeper dive into the client-server model through exploring
a part of HTTP that you’ve probably seen before: <em>HTTP status
codes</em>.
</p>
<p class="p__1qg33Igem5pAgn4kPMirjw">
When a server responds to a client, the server specifies a status code
as a part of the response. Status codes indicate whether or not the HTTP
request was successfully completed and if there was an error, they
contain some information about the type of error that happened. The
status code helps the browser know how to handle the data that was sent
back with the response.
</p>
<p class="p__1qg33Igem5pAgn4kPMirjw">
Review the HTTP statuses below and see if any of them seem familiar.
</p>

<img src="https://content.codecademy.com/programs/code-foundations-path/web-dev-survey/table.svg" alt="a table showing the most common HTTP status codes" class="img__1JGFO2nlisObc3KeOSGPRp">

<ol class="ol__1XI8Ausmo9cwwog3NvDzWF">
<li class="li__1KqBjwbWA3ze6V0BvXq9Rx">
<p class="p__1qg33Igem5pAgn4kPMirjw">
The browser is currently displaying a website that Alex has created to
show photos and descriptions of her pets. If you click on the links for
<code class="code__2rdF32qjRVp7mMVBHuPwDS">Dogs</code> or
<code class="code__2rdF32qjRVp7mMVBHuPwDS">Cats</code>, you can see more
information about Alex’s dogs and cats.
</p>
</li>
<li class="li__1KqBjwbWA3ze6V0BvXq9Rx">
<p class="p__1qg33Igem5pAgn4kPMirjw">
Next, click on the file icon in the upper left corner of the text
editor. You’ll see the different HTML files that the server is ready to
send to the browser whenever those links are clicked. These HTML files
correspond to the different web pages that are displayed in the browser.
When the <code class="code__2rdF32qjRVp7mMVBHuPwDS">Dogs</code> link is
clicked, the server will send the
<code class="code__2rdF32qjRVp7mMVBHuPwDS">dogs.html</code> file to the
client.
</p>
</li>
<li class="li__1KqBjwbWA3ze6V0BvXq9Rx">
<p class="p__1qg33Igem5pAgn4kPMirjw">
Try out the <code class="code__2rdF32qjRVp7mMVBHuPwDS">Dogs</code> and
<code class="code__2rdF32qjRVp7mMVBHuPwDS">Cats</code> links now!
</p>
</li>
<li class="li__1KqBjwbWA3ze6V0BvXq9Rx">
<p class="p__1qg33Igem5pAgn4kPMirjw">
Let’s create a 404 status response by making a request for a
non-existent resource. Alex hasn’t built a webpage to list her turtles!
Click on the link for
<code class="code__2rdF32qjRVp7mMVBHuPwDS">Turtles</code> to see the
browser display the 404 status code.
</p>
</li>
</ol>

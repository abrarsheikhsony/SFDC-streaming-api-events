# Salesforce Streaming API Events

## Streaming API
<ul>
<li>Streaming API is a specialized API for setting up notifications that trigger when changes are made to Salesforce data.</li>
<li>It uses a publish-subscribe, or pub/sub, model in which users can subscribe to channels that broadcast certain types of data changes.</li>
<li>The pub/sub model reduces the number of API requests by eliminating the need for polling.</li>
<li>Streaming API is great for writing apps that would otherwise need to frequently poll for changes.</li>
</ul>

## When to use Streaming API
<ul>
<li>Use Streaming API to receive near-real-time streams of data that are based on changes in Salesforce records or custom payloads.</li>
<li>For Salesforce record changes, Salesforce publishes notifications when the changes occur.</li>
<li>For custom notifications, you can publish event messages.</li>
<li>Subscribers can receive notifications using CometD—an implementation of the Bayeux protocol that simulates push technology.</li>
<li>Clients can subscribe to some types of events with Apex triggers or declaratively with Process Builder and flows.</li>
</ul>

## Streaming Events Features
<ol type="1">

<li>PushTopic</li>
<ul>
<li>Receive changes to Salesforce records based on a SOQL query that you define. <b>The notifications include only the fields that you specify in the SOQL query.</b></li>
</ul>

<li>Change Data Capture (CDC)</li>
<ul>
<li>Receive changes to Salesforce records <b>with all changed fields</b>. Change Data Capture supports more standard objects than PushTopic events and provides more features, such as <b>header fields that contain information about the change.</b></li>
<li>Change Data Capture is part of a pilot program. To participate in the pilot, contact Salesforce.</li>
</ul>

<li>Platform Event</li>
<ul>
<li>Publish and receive <b>custom payloads with a predefined schema</b>. The data can be anything you define, including business data, such as order information. Specify the data to send by defining a platform event. Subscribe to a platform event channel to receive notifications.</li>
</ul>

<li>Generic Event</li>
<ul>
<li>Publish and receive <b>arbitrary payloads without a defined schema.</b></li>
</ul>

</ol>

## Streaming API Protocols
<ul>
<li>Bayeux is a protocol for transporting asynchronous messages, primarily over HTTP.</li>
<li>CometD is a scalable HTTP-based event routing bus that uses an AJAX push technology pattern known as Comet. It implements the Bayeux protocol.</li>
<li>Long polling, also called Comet programming, allows emulation of an information push from a server to a client. Similar to a normal poll, the client connects and requests information from the server. However, instead of sending an empty response if information isn't available, the server holds the request and waits until information is available (an event occurs). The server then sends a complete response to the client. The client then immediately re-requests information. The client continually maintains a connection to the server, so it’s always waiting to receive a response. In the case of server timeouts, the client connects again and starts over.</li>
</ul>
	
## High Level Overview Events Features
<table>
	<tr>
		<th>API</th>
		<th>Protocol</th>
		<th>Data Format</th>
		<th>Communication</th>
	</tr>
	<tr>
		<td>Streaming API</td>
		<td>Bayeux</td>
		<td>JSON</td>
		<td>Asynchronous (stream of data)</td>
	</tr>
	<tr>
		<td>Platform Events</td>
		<td>CometD</td>
		<td>JSON</td>
		<td>Asynchronous (stream of data)</td>
	</tr>
</table>




## Useful Resources
<ul>
<li><a href="https://trailhead.salesforce.com/content/learn/modules/api_basics/api_basics_overview" target="_blank" alt="API Basics: When to Use Streaming API">API Basics: When to Use Streaming API</a></li>
<li><a href="https://trailhead.salesforce.com/content/learn/modules/api_basics/api_basics_streaming" target="_blank" alt="API Basics: Use Streaming API">API Basics: Use Streaming API</a></li>
<li></li>
</ul>

<img src="supportedimages/118.png"/>

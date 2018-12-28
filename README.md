# Salesforce Streaming API Events

## Streaming API
<ul>
<li>Streaming API is a specialized API for setting up notifications that trigger when changes are made to Salesforce data.</li>
<li>It uses a publish-subscribe, or pub/sub, model in which users can subscribe to channels that broadcast certain types of data changes.</li>
<li>The pub/sub model reduces the number of API requests by eliminating the need for polling.</li>
<li>Streaming API is great for writing apps that would otherwise need to frequently poll for changes.</li>
</ul>

## Difference b/w Push and Pull Technology
<ul>
<li><b>Push technology (also called the publish/subscribe model)</b>, transfers information that is initiated from a Server to the Client.</li>
<li><b>Pull technology (also called constant/frequently polling)</b>, in which a request for information is made from a Client to the Server.</li>
</ul>

## Streaming API Protocols
<ul>
<li>Bayeux is a protocol for transporting asynchronous messages, primarily over HTTP.</li>
<li>CometD is a scalable HTTP-based event routing bus that uses an AJAX push technology pattern known as Comet. It implements the Bayeux protocol.</li>
<li>Long polling, also called Comet programming, allows emulation of an information push from a server to a client. Similar to a normal poll, the client connects and requests information from the server. However, instead of sending an empty response if information isn't available, the server holds the request and waits until information is available (an event occurs). The server then sends a complete response to the client. The client then immediately re-requests information. The client continually maintains a connection to the server, so it’s always waiting to receive a response. In the case of server timeouts, the client connects again and starts over.</li>
<li>You can read more about long polling, Bayeux, or CometD, in the <a href="https://docs.cometd.org/" target="_blank" alt="CometD documentation.">CometD documentation.</a></li>
</ul>

## Applications for Streaming API
<ul>
<li><b>Applications That Poll Frequently:</b> Applications that have constant polling action against the Salesforce infrastructure, consuming unnecessary API calls and processing time, would benefit from Streaming API because it reduces the number of requests that return no data.</li>
<li><b>General Notification:</b> Use Streaming API for applications that require general notification of data changes in an org to reduce the number of API calls and improve performance.</li>
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
<li>A PushTopic triggers notifications for changes in Salesforce records resulting from a create, update, delete, or undelete operation. A PushTopic <b>notification is based on the criteria that you specify in the PushTopic record and the SOQL query that you define.</b> Only the fields specified in the query are included in the notification. The PushTopic defines a subscription channel.</li>
<li>Supported Objects: Account, Contact, Opportunity, Custom Objects</li>
</ul>

<li>Change Data Capture (CDC)</li>
<ul>
<li>Receive changes to Salesforce records <b>with all changed fields</b>. Change Data Capture supports more standard objects than PushTopic events and provides more features, such as <b>header fields that contain information about the change.</b></li>
<li>Starting with <a href="https://releasenotes.docs.salesforce.com/en-us/spring19/release-notes/rn_data_change_events.htm" target="_blank" alt="Spring '19 release">Spring '19 release</a> Change Data Capture is now Generally Available (GA).</li>
</ul>

<li>Platform Event</li>
<ul>
<li>Publish and receive <b>custom payloads with a predefined schema</b>. The data can be anything you define, including business data, such as order information. Specify the data to send by defining a platform event. Subscribe to a platform event channel to receive notifications.</li>
<li>A Salesforce entity that represents the definition of the custom data that you send in a platform event message. You create a platform event and define its fields in Salesforce. The subscription channel is based on the platform event name.</li>
</ul>

<li>Generic Event</li>
<ul>
<li>Publish and receive <b>arbitrary payloads without a defined schema.</b></li>
</ul>

<li>High-Volume Platform Events</li>
<ul>
<li>Use high-volume platform events to publish and process millions of events efficiently.</li>
<li>Starting with <a href="https://releasenotes.docs.salesforce.com/en-us/spring19/release-notes/rn_messaging_high_volume_events.htm" target="_blank" alt="Spring '19 release">Spring '19 release</a> High-Volume Platform Events is now Generally Available (GA).</li>
</ul>

</ol>

## Subscribe to and Replay Events Using a Lightning Component
<ul>
<li>The <a href="https://developer.salesforce.com/docs/component-library/bundle/lightning:empApi/documentation" target="_blank" alt="lightning:empApi component">lightning:empApi component</a> uses a shared CometD-based Streaming API connection, enabling you to run multiple streaming apps in the browser.</li>
<li>To call the component’s methods, add the lightning:empApi component inside your custom component and assign an aura:id
attribute to it.</li>
<li><img src="supportedimages/Lightning_empApi.png"/></li>
<li>Then in the client-side controller, add functions to call the component methods.</li>
</ul>

## Subscribe to and Replay Events Using a Visualforce Page



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
<li><a href="https://developer.salesforce.com/docs/atlas.en-us.api_streaming.meta/api_streaming/intro_stream.htm" target="_blank" alt="Streaming API Developer Guide">Streaming API Developer Guide</a></li>
</ul>

<img src="supportedimages/118.png"/>

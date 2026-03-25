<html lang="en">
<script type='text/javascript'>
	function sendMessageToUser(message) {
		embeddedservice_bootstrap.utilAPI.sendTextMessage(message)
		.then(() => {
			console.log("Message sent");
		})
		.catch(() => {
			console.log("Message not sent");
		})
		.finally(() => {
			console.log("Message sent - finally");
		});
	}
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

            /* START:: Conversation Routed Listener */
            window.addEventListener("onEmbeddedMessagingConversationRouted", (event) => {
                console.log( "Conversation Routed" );
                console.log( "Event detail: ", JSON.stringify( event.detail ) );

				const payloadString = event.detail.conversationEntry.entryPayload;
				const innerData = JSON.parse(payloadString);
				const routingType = innerData.routingType;
				console.log(routingType);

				if ( routingType == "Initial" ) {
                	sendMessageToUser('Initial Transfer');
				} else if ( routingType == "Transfer" ) {
                	sendMessageToUser('Subsequent Transfer');
				} 
            });
            /* END:: Conversation Routed Listener */

			embeddedservice_bootstrap.init(
				'00DgL00000DFmfx',
				'MIAW',
				'https://infallibletechiechat-dev-ed.develop.my.site.com/ESWMIAW1760131052896',
				{
					scrt2URL: 'https://infallibletechiechat-dev-ed.develop.my.salesforce-scrt.com'
				}
			);
		} catch (err) {
			console.error('Error loading Embedded Messaging: ', err);
		}
	};
</script>
<script type='text/javascript' src='https://infallibletechiechat-dev-ed.develop.my.site.com/ESWMIAW1760131052896/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
</html>

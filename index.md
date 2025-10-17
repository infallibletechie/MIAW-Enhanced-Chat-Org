<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Salesforce Embedded Messaging Setup</title>
</head>
<body>
    <script type='text/javascript'>
        function initEmbeddedMessaging() {
            try {
                embeddedservice_bootstrap.settings.language = 'en_US';

                window.addEventListener("onEmbeddedMessagingSessionStatusUpdate", (event) => {
                    console.log("Payload:", event.detail);
                });

                embeddedservice_bootstrap.init(
                    '00DgL00000DFmfx',
                    'MIAW',
                    'https://infallibletechiechat-dev-ed.develop.my.site.com/ESWMIAW1760131052896',
                    {
                        scrt2URL: 'https://infallibletechiechat-dev-ed.develop.my.salesforce-scrt.com'
                    }
                );
            } catch (err) {
                console.error('Error loading Salesforce Embedded Messaging:', err);
            }
        }
    </script>
    <script
        type='text/javascript'
        src='https://infallibletechiechat-dev-ed.develop.my.site.com/ESWMIAW1760131052896/assets/js/bootstrap.min.js'
        onload='initEmbeddedMessaging()'
    ></script>

</body>
</html>

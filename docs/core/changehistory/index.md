# 0.186.0 Change Notes

## Allowed backend applications to specify HTTPS_PROXY
Applications can now configure backend HTTP requests to go through a firewall proxy server with the HTTPS_PROXY environment.
To enable this, the backend application must call the following API as part of it's initialization:
  ```imodeljs-clients-backend: RequestHost.initialize();```

## More diagnostics and trace logging of all HTTP requests
* Added API to detect and use fiddler proxy (if available) at the backend to route requests for troubleshooting.
To enable this, the backend application must call the following API as part of it's initialization:
  ```imodeljs-clients-backend: RequestHost.initialize();```

  The API is called automatically when opening iModel-s, but must be typically setup by backend applications at startup.

* Setup trace logs of all requests made through the Request API. To enable this, do:
   ```Logger.setLevel("imodeljs-clients.Request", LogLevel.Trace);```

## Removed IModelDb's cache of accessToken
For long running operations like AutoPush, the developer must explicitly supply an ```IAccessTokenManager``` to keep the token current.

# Best Practice
In order to get the best user experience when using the local interface of your Bosch Eyes Camera, we have a few best practice tips for you. These tips should be considered and implemented in any public open source project that interacts with the Eyes Camera.

## Watch this repository
First of all, watch this repository to get notified when we change or update our Terms and Conditions or when there are changes or updates in the API. In case the Terms and Conditions are changed, the commit message will always contain the keyword `T&C`. In case the API is changed or updated, the commit message will always contain the keyword `API`.

## Limit the number of requests in a given time period
Keep the number of requests in a given time period low. You should also consider that a large number of requests flood the log file. In the event of a support request, the error may no longer be found in the log file, making an error analysis difficult.

## Host Verification
The communication with the Eyes Camera is cryptographically protected via TLS. It is recommended that your implementation verifies the certificate chain. Find the Root-Certificate to trust below. Be aware that the common name is set to the MAC-Address of the camera.


### Root Certificate
```
-----BEGIN CERTIFICATE-----
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
BPePFXgk
-----END CERTIFICATE-----
```


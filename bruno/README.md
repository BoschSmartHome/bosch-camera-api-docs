# Bruno Collection

This folder contains a Bruno collection for testing the local Bosch Eyes Camera API directly against your camera.

## Prerequisites

Before using the collection, make sure the following is available:

1. The **Local Data Interface** is enabled on the camera.
2. You have the local API username and password.
3. Bruno is installed on your computer.

If you still need to enable local API access, see the user setup instructions in `../user_creation/README.md`.

## Open The Collection

1. Start Bruno.
2. Open the collection in the `bruno/` folder.
3. Select **GEN2 Camera EU Data Act Endpoints**.

## Configure The Variables

The collection uses variables for the camera connection and authentication.

1. Open the collection variables in Bruno.
2. Set `camera_host` to the IP address of your camera.
3. Set `username` to your local API user name.
4. Set `password` to your local API password.
5. Save the changes.

The collection is already configured to use **HTTP Basic Auth** with these variables, so you only need to provide the correct values.

## Send A Request

1. Choose an endpoint from the collection.
2. Click **Send**.
3. Review the response in Bruno.

If the request succeeds, Bruno will show the response returned by the camera. This lets you verify that the connection, authentication, and selected endpoint are working correctly.

## Troubleshooting

If a request does not work, check the following:

1. The camera is reachable from your device on the same network.
2. `camera_host` is set correctly.
3. The local API username and password are correct.
4. The **Local Data Interface** is enabled on the camera.
5. The response in Bruno contains an authentication, network, or TLS-related error message.

